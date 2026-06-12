---
title: "Announcment. fold@home .deb package available here :)"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Tomatz on 2008-03-21
Folding@home is a well known cluster project it uses "idle" computer processing power to help scientists better understand diseases like Alzheimer's better (of which my grandfather suffered). All in all it is a highly worthwhile project :)   

[http://folding.stanford.edu/English/Download](http://folding.stanford.edu/English/Download)

Unfortunately there was no .deb package for folding@home also i wanted to have a go at creating my first .deb. So it was suggested to me that i should make one (original post below).

[http://ubuntuforums.org/showthread.php?p=4557299#post4557299](http://ubuntuforums.org/showthread.php?p=4557299#post4557299)

Sipmly:

Download (below)

Install

Open a terminal (preferably in an empty directory in home) and type  ** foldathome**

Enjoy :)

*Any criticism/help is **truly** appreciated*


[B][EDIT]

Sorry as you can see below i didn't read the license properly (at all) before creating this package. So before I and the ubuntu community get sued, water tortured, boiled in oil etc I have removed it. :(

Hopefully i will be back soon with a workaround :)[/B]

---

### Post by oldb0y on 2008-03-21
This is great Tomatz:)
There is a thread in the cafe for TeamUbuntu in the folding project, you might want to make this announcement there as well. link: [http://ubuntuforums.org/showthread.php?t=102313&page=106](http://ubuntuforums.org/showthread.php?t=102313&page=106)
And again, thanks a lot!

---

### Post by Tomatz on 2008-03-21
Your welcome :)

Have posted details on the folding@home teamubuntu thread.

---

### Post by jpkotta on 2008-03-21
You can't do that.  Read the license.  This is why all other installers jump through hoops to download it from Stanford.

```

[jpkotta@gauss bin](1)$ /opt/foldingathome/config/fah6 -license

Note: Please read the license agreement (fah6 -license). Further 
use of this software requires that you have read and accepted this agreement.

----------------------------------------------------------------------
Folding@Home distributed computing client

Copyright 1999-2007 Stanford University.  All Rights Reserved.

License Agreement:

...

Distribution of this software is prohibited. It may only be
obtained by downloading from http://folding.stanford.edu.


```

---

### Post by Tomatz on 2008-03-21
Thanks for the info.  I just assumed it was foss :(

I wont let it discourage me :)

As i said it was the first package i have created so it was good from an educational point of view. 

I suppose it shouldn't be too hard to create a .deb with a script in it to download the executable from the folding@home website also i think i could structure the installation better giving it (folding@home) a dedicated directory to work from.

:guitar:

---

### Post by jpkotta on 2008-03-29
You are more than welcome to package one of the installer scripts.  See [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by Tomatz on 2008-03-29
Thanks :)

I'll look into that

---

