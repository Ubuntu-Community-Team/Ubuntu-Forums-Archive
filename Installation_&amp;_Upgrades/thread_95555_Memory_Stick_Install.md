---
title: "Memory Stick Install"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by brianlparkinson on 2005-11-26
I am trying to install to a laptop (without cd drive) using a memory stick (1gb). I have everyting on the stick as per directions elsewhere on the site but the stick will not boot. 
I have downloaded the mbr package from the debian site. 
My only Linux installed so far is the ubuntu 'live' which is running on my other desktop. The mbr package is a tarball but I do not seem to have the commands available to build the 'runtime' code. As you can tell I am a newbie to Linux.
Does anyone have a lump of code which I can just run in order to fix the boot sector of my memory stick - or am I just missing something, it is getting rather late here in the uk :)   
Tired but determined to get this thing working - Brian

---

### Post by brianlparkinson on 2005-11-28
Ok - a reply to my own thread but now I have got this working I should share the info.
Problem
IBM Thinkpad X24 no cd drive, external fdd, usable USB port which can be booted from. Also have 1gb Memory stick which I can use.
Solution
1. Format the memory stick and make bootable using PeToUSB
   ([http://codebeetle.com/page.php?al=petousb)](http://codebeetle.com/page.php?al=petousb)). Note the HP USB format
   and boot tool did not work with my stick.
2. Expand 'boot.img.gz' using IZarc and then open 'boot.img' with MagicISO 
    (available from download.com 
    [http://www.download.com/3000-2646-10191803.html)](http://www.download.com/3000-2646-10191803.html)). The files were 
     then copied onto the memory stick.
3. Plug laptop into the my router (cable not wireless).
4. Set the laptop to boot from USB.
5. Boot from the memory stick. This installed the base software but left me 
    with a $ prompt when the package download failed part way through.
6. Collected the rest of the download using
      sudo apt-get update
      sudo apt-get -f install
      sudo install ubuntu-desktop
    Note this takes some time even with a fast broad band. Download speed 
    about 250 and time about 30 minutes.
7. System auto configured with just a few questions to answer. Note I opted 
    for 8 gb boot primary Ext2; 2gb swop and 20gb home primary Ext2 
    directory structure. I ma sure others will have a much more mature view 
     on this.
 
Hope this helps anyone out there with the same issues.

Regards
Brian
ps If you have problems with X24 BIOS passwords then thre is a solution also

---

