---
title: "Unable to compile and install GRASS GIS"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by iain.mjbanks on 2010-03-06
please forgive me if im being a total n00b.

im installing GRASS using the instructions found here: [http://grass.osgeo.org/wiki/Compile_and_Install_Ubuntu](http://grass.osgeo.org/wiki/Compile_and_Install_Ubuntu)

when i get to the configuration step:
> 
 CFLAGS="-g -Wall" ./configure \
     --with-cxx --with-freetype=yes \
     --with-postgres=no --with-sqlite=yes --enable-largefile=yes \
     --with-tcltk-includes=/usr/include/tcl8.4 \
     --with-freetype-includes=/usr/include/freetype2 \
     --with-python=/usr/bin/python2.5-config \
     --with-wxwidgets=yes \
     --with-nls --enable-largefile \
     --with-proj-share=/usr/share/proj
it stops and gives me this message:

> 
...
checking if system supports Large Files at all... yes
checking whether to use Python... yes
checking for python-config... /usr/bin/python2.5-config
./configure: 16055: /usr/bin/python2.5-config: not found
checking for Python.h... no
configure: error: *** Unable to locate Python includes.i did a search of my filesystem and couldnt find any files with that name, though i do believe i have python installed.  

i then ran the following:

> CFLAGS="-g -Wall" ./configure -with-tcltk-includes=/usr/include/tcl8.4


and was able to proceed with the installation.  while i was able to launch the GUI, it would not read the raster layer of the files.  im assuming this is a dependency problem, but im still not quite sure i understand how all this works.  

please forgive my ignorance!

---

### Post by Herman on 2010-03-06
:D What's wrong with just installing grass by clicking on it in synaptic package manager, or just typing 'sudo apt-get install grass' ?
Grass is in the official Ubuntu repositories, unless for some reason you need the bleeding edge version of grass for some reason maybe? 
```
sudo apt-get install grass
```I use Quantum GIS. 
Quantum GIS is a nice GUI mapping program and it's comparable to MapInfo in Windows, although quite a bit different to use. Quanum GIS works on top of grass I think. I normally install grass when I install Quantum GIS.

---

### Post by iain.mjbanks on 2010-03-06
i first tried 'sudo apt-get install grass' but i had the same problem that it wouldnt read the raster layer.  im getting the feeling this has nothing to do with my installation.

---

### Post by Herman on 2010-03-06
Okay, I opened grass and I'm having a look around in it.

From the grass website I found this, [Raster data processing in GRASS GIS]("http://grass.ibiblio.org/grass63/manuals/html63_user/rasterintro.html") in case it's any help to you. 

Are you wanting to use grass because it's required for a university course or something?
If you're trying to actually get work done maybe I can help you georeference a raster image in Quantum GIS, but I'm not up to speed with grass. 

UPDATE: I have now managed to get a raster image opened in grass somehow, but I'm not exactly sure how I did it. 
As far as I can remember I did something like 'File'-->'import raster image'-->'Multiple formats using GDAL', and then I'm not sure what I did but I have a nice raster map up. Sorry I'm not able to be more helpful so far.  I have absolutely no idea what I'm doing, so it's a classic case of the blind leading the hard of seeing. (LOL).

UPDATE:
After a few more repeats I think I'm getting the hang of it,
1. File --> Import raster map --> Multiple formats GDAL
  ( an 'r.in.gdal' dialog opens)
2. under the 'required' tab, 
  (i) in feild 1, browse to your raster file
  (ii) in filed 2 we can make anything up, a name for your output raster 
  (iii) click the 'Run' button in the bottom right-hand corner and it should grey out for a minute or two
3. Click 'Close'. 

In GRASS 6.4 ORC5 GIS Manager dialog,
1. I clicked on 'Add raster layer' icon.
2. In 'Base Map' field, (down near the bottom), clicked on the button before the field and select the red layer from the 'select item' menu.
3. I repeated steps 1 and 2 for green and also for blue layers
4. I went to the Map Display frame and selected the pan tool and clicked somewhere inside the frame and my raster image appeared.

Note I have not yet georeferenced this raster image, ( I don't know how to do that yet).

---

### Post by johanvdw on 2010-04-23
Please note that you might find more recent versions of Grass in the ubuntugis repositories:
[https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable](https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable)

---

