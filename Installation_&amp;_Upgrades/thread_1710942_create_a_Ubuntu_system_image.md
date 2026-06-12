---
title: "create a Ubuntu system image"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-20
I am learning a bunch of stuff about Ubuntu and I am making critical errors to the system.  I am getting tired of reinstalling Ubuntu, LAMP and my website every time I make a mistake.  I had to reinstall Ubuntu too many times in the last month.  So I need to implement a better way of recovering from my mistakes.

I would like to create an image of my system that I can recover from when I make my next critical error.

Any idea how to do this?

Thanks,

Spindler

---

### Post by JRV on 2011-03-20
Try the Clonzilla disk.

Or boot from a live CD and use dd. 

Read the man page carefully before using dd. And then run gparted to check and make sure you have the right partitions.  dd can mess thing up if you enter a wrong command.

Make sure you understand it before trying it.

---

### Post by falko on 2011-03-20
I'd suggest:
- CloneZilla: [http://www.howtoforge.com/cloning-linux-systems-with-clonezilla-server-edition-clonezilla-se](http://www.howtoforge.com/cloning-linux-systems-with-clonezilla-server-edition-clonezilla-se)
- Ghost4Linux: [http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux](http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux)
- Maybe SystemImager: [http://wiki.systemimager.org/index.php/Main_Page](http://wiki.systemimager.org/index.php/Main_Page)
- dd (you can even use it over the network with netcat, see [http://www.howtoforge.com/ghosting-the-machine](http://www.howtoforge.com/ghosting-the-machine) )

---

### Post by listerdl on 2011-04-04
> **falko said:**
> I'd suggest:
- CloneZilla: [http://www.howtoforge.com/cloning-linux-systems-with-clonezilla-server-edition-clonezilla-se](http://www.howtoforge.com/cloning-linux-systems-with-clonezilla-server-edition-clonezilla-se)
- Ghost4Linux: [http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux](http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux)
- Maybe SystemImager: [http://wiki.systemimager.org/index.php/Main_Page](http://wiki.systemimager.org/index.php/Main_Page)
- dd (you can even use it over the network with netcat, see [http://www.howtoforge.com/ghosting-the-machine](http://www.howtoforge.com/ghosting-the-machine) )

Which is the 'easiest' to use? By that I mean, one that you cant go wrong with. Cloenzilla is excellent but I think for the average user there are tooo many options and you can make errors quite easily. Thanks

---

