BFirst attempt at grabbing vertex from netcdf:

gmt grd2xyz /mnt/courses/eos2680/ETOPO1/topo_1deg_ice_gline.nc | awk '{print "v"$1/360" "$2/90" "$3/1000" "1.0}' > tmp.obj

Works fine but you also need to include face information, e.g.

f 1 2 3 4

For each face linking each vertex.  I assume the order of the vertex listing
gives the vertex number.  This is a bit like pixel and gridline registration
where both a needed.

In this case, we need something more sophisticated than a shell script line...

Also, we need to test if it is possible to go inside an object or have hollow objects.

Remove the bottom face of the cube.obj to see if that is possible.
