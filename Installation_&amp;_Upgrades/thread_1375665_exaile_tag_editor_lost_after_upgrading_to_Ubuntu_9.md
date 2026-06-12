---
title: "exaile tag editor lost after upgrading to Ubuntu 9.10"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by tomzhi on 2010-01-08
My exaile tag editor lost after upgrading to Ubuntu 9.10. 

I had been using 9.04. My exaile used to have a tag editor which allows me to edit tags for multiple files simultaneously, and fill tags by patterns of file names. I used to highlight songs in the playlist, and then right click, there would show "Information" and when I click on it, it's the tag editor. 

After the upgrade, I am not sure if I am missing some plugins or whatever, the tag editor is no long here. Now, I only see "Properties" when I right click, which only allows me to edit one song at a time. Please help. I like Exaile very much so far.

---

### Post by quemaneumaticos on 2010-02-21
Hi,

I have just upgraded from 8.04 and i have the same problem. I cant edit metadata and there is a lot of files that their tagg is not correct now(before their was). Also, hotkeys dont work anymore.





P.D.Sorry for my english

---

### Post by tomzhi on 2010-04-08
Solved:

the version in the 9.10 distribution does not include the exfalso plugin.

to fix:

1. install exfalso
   sudo apt-get install exfalso
2. compile the newest exaile (v0.3.1.0)
   [http://launchpad.net/exaile/0.3.1/0.3.1.1/+download/exaile-0.3.1.1.tar.gz](http://launchpad.net/exaile/0.3.1/0.3.1.1/+download/exaile-0.3.1.1.tar.gz)
3. cp the following folder in the downloaded file to your ~/.local/share/exaile/plugins folder:
   exaile-0.3.1.1/plugins/exfalso

4. open exaile, go to Edit --> Preference --> Plugin 
   find ExFalso tag editor and check it. now try again!

---

