<?php
function findDirtyCell($posR, $posC, $otherR, $otherC)
{

    if (intval($posR) < intval($otherR)) echo "DOWN" . PHP_EOL;
    else if (intval($posR) > intval($otherR)) echo "UP" . PHP_EOL;
    else if (intval($posR) == intval($otherR))
    {   
        if (intval($posC) == intval($otherC)) echo "CLEAN" . PHP_EOL;
        else 
        {
            if (intval($posC) > intval($otherC)) echo "LEFT" . PHP_EOL;
            elseif (intval($posC) < intval($otherC)) echo "RIGHT" . PHP_EOL;
        }
  
    }

}
    
function getDirtyCells($board)
{
    $dirtyArr = [];
    
    for($i = 0; $i < 5; $i++)
    {
        for($j = 0; $j < 5; $j++)
        {
            if ($board[$i][$j] == 'd') $dirtyArr[] =  $i . "|" . $j;
        }
    }
    
    return $dirtyArr;
}
    
    
function distanceDiff($posR, $posC, $otherR, $otherC)
{
    $diffR = abs($posR - $otherR);
    $diffC = abs($posC - $otherC);
    
    return ($diffR + $diffC);

}

function getCoords($coord)
{  
    $res = explode("|", $coord);
    
    return array('row' => $res[0], 'col' => $res[1]);
    
}

function getMinDistance($posR, $posC, $arr)
{
    $distancesArr = [];
    
    foreach($arr as $coords)
    {    
        $coord = getCoords($coords);
        
        $distance = distanceDiff($posR, $posC, $coord['row'], $coord['col']);
        
        $key = $coord['row'] . "|" . $coord['col'];
        
        $distancesArr[$key] = $distance;        
    }
    
    $min = min($distancesArr);
    $coords = array_search($min, $distancesArr);
    
    return array($coords => $min);
}
    
function next_move(&$posr, &$posc, &$board) {
    
    $dirtyArr = getDirtyCells($board);
    
    $closestDirtyCell = getMinDistance($posr, $posc, $dirtyArr);
    
    $closestCell = getCoords(key($closestDirtyCell));
    
    findDirtyCell($posr, $posc, $closestCell['row'], $closestCell['col']);
    
    //return 0;
}

$fp = fopen("php://stdin", "r");

$temp = fgets($fp);              //moves made by the second player
$position = explode(' ',$temp);

$board = array();

for ($i=0;$i<5;$i++) {
    fscanf($fp, "%s", $board[$i]);
}

next_move($position[0], $position[1], $board);
?>
