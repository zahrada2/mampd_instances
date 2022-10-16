# mampd_instances
This repository contains MAMPD instance files.

# format
 - For each map, there are 10 instances - e.g. map den_30_random_1 has instances map0_180, map1_180 ... map9_180.
 - The instance names are in the following format: mapX_Y, where X is the number of the instance and Y is the number of items in the instance.
 - Files with .map extension contain information about the map. **All map files are the same for each map type.** This means that map0_180.map is equal to map4_180.map.
 - Files with .tsp extension contain information about the instance itself.
 - Images of each instance are in a png_ps subdirectory. Black squares are obstacles, red squares are items, blue squares are agent starting locations and green squares are agent ending depots.

## map files
- The map files are in standard MAPF format as seen in https://movingai.com/benchmarks/mapf.html .
- The format specifications are listed below:

Each map begins with a preamble specifying its parameters and ending with a keyword "map":
type octile
height X
width Y
map

Then, the map is encoded with 'T' denoting an obstacle and '.' denoting a free space.

## instance files

### PREAMBLE
The instances begin with a preamble specifying meta-information about each instance.
Dimension of the instance denotes the number of all nodes in the map - all items, starting depots and ending depots.

### NODE_COORD_SECTION
List of all nodes of the map begins with NODE_COORD_SECTION, where each row denotes one node and its location, and has the following format:
ID Y/ROW X/COLUMN

Note that ID starts from 1, and therefore, the last element should have ID equal to the dimension of the instance.

This section ends with the keyword START_DEPOT_SECTION.

### START_DEPOT_SECTION
In this section, each row contains one ID signifying a starting location of an agent.
The ID points to the ID of nodes in **NODE_COORD_SECTION**.

This section ends with row containing only **-1**.

### END_DEPOT_SECTION
Analogous to **START_DEPOT_SECTION**, this section contains information about agents ending depots - final goals.
Each row contains an ID of one node from **NODE_COORD_SECTION**, and this section ends with a row containing only **-1**.

The whole file ends with **EOF** keyword.


# TODO:
Add images of the rest of instances
