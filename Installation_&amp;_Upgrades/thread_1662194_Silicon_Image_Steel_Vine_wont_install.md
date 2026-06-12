---
title: "Silicon Image Steel Vine wont install"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by sixteenornumber on 2011-01-07
I am very new to linux so please assume that I haven't tried a whole lot.  I Bought a Icy Dock external HDD enclosure with a Silicon Image 5744 Chipset.  The USB is working fine on Ubuntu however I can only seem to get the ESATA to work on my win7 laptop. 

The Icydock web site has a configuration manager for linux 32/64 here [http://www.icydock.com/product/mb662us-2s_frame.html](http://www.icydock.com/product/mb662us-2s_frame.html)

I downloaded it, opened the tar to find a PDF with the following directions,

> Linux
Use the following procedure to launch the SteelVine Manager on a Linux system.
1. Change to the directory in which the SteelVine Manager GUI and daemon software was installed (such as /usr/local/SiliconImage)
2. Start the daemon by entering the command: ./SiI57XX -e
3. Open a new terminal window and start the GUI by entering the command: ./SiI57XXUII did exactly that I all I get is, 

```

$cd /usr/local/SiliconImage
$ls
icons
SiI Config
SteelVine
SteelVineManager
SteelVineManagerHelp.pdf
sv2000.xpm
Translations
$
$ ./SteelVine
bash: ./SteelVine: No such file or directory
```

---

