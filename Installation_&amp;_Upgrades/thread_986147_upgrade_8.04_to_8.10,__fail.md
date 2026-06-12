---
title: "upgrade 8.04 to 8.10,  fail"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by xjspace on 2008-11-18
1.sudo mkdir /media/cdrom0 
2.sudo mount -t iso9660 -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0/
3.sudo apt-cdrom -m -d /media/cdrom0 add 
4.sudo apt-get update 
5.sudo /media/cdrom/cdromupgrade
step 3
x-desktop:~$ sudo apt-cdrom -m -d /media/cdrom0 add
[sudo] password for x: 
&#29616;&#25226; /media/cdrom0/ &#20316;&#20026;&#20102; CD-ROM &#30340;&#25346;&#36733;&#28857;
&#27491;&#22312;&#37492;&#21035;.. [789f0853e2eebf2d7df1c1d361e2f4df-2]
&#27491;&#22312;&#20809;&#30424;&#20013;&#26597;&#25214;&#32034;&#24341;&#25991;&#20214;..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc
upgrades fail
check
md5sum  is ok (it is right)

---

### Post by pastalavista on 2008-11-18
bootable cd's can't be upgraded. you have to do an actual install and then make a new .iso of the installation

edit:
never mind. I didn't understand what you were doing. If you are using 8.04 and load a different Ubuntu installation disk, it should ask if you want to add it as a repository and then add it to the software sources. In Synaptic, be sure the software sources include the CD ROM (check the box).

then try,

```
sudo aptitude dist-upgrade
```

I've been told that doesn't work any more, but that was how I upgraded and it worked perfectly for me.

---

### Post by tqzxzjhu on 2008-11-18
[&#27927;&#25163;&#27744;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#28020;&#32568;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#38452;&#27807;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#19978;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#19979;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)

---

### Post by xjspace on 2008-11-19
Thanks
After I go home, tries..............

---

### Post by Partyboi2 on 2008-11-19
If you are trying to upgrade using the alternate cd you can stick the cd in the cdrom and in a terminal type
```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by xjspace on 2008-11-19
1.wa.
 sudo apt-cdrom -m -d /media/cdrom0 add     


&#28155;&#21152;&#20809;&#30424;&#22833;&#36133;

&#28155;&#21152;&#20809;&#30424;&#26102;&#20986;&#38169;&#65292;&#21319;&#32423;&#20013;&#27490;&#12290;&#22914;&#26524;&#23427;&#26159;&#19968;&#20010;&#21487;&#29992;&#30340; Ubuntu &#20809;&#30424;&#65292;&#37027;&#20040;&#35831;&#25253;&#21578;&#26412;&#38169;&#35823;&#12290;

&#38169;&#35823;&#28040;&#24687;&#26159;&#65306;
'Unable to locate any package files, perhaps this is not a Ubuntu Disc or the wrong architecture?'



2.alt +f2
gksu "sh /cdrom/cdromupgrade"


&#28155;&#21152;&#20809;&#30424;&#22833;&#36133;

&#28155;&#21152;&#20809;&#30424;&#26102;&#20986;&#38169;&#65292;&#21319;&#32423;&#20013;&#27490;&#12290;&#22914;&#26524;&#23427;&#26159;&#19968;&#20010;&#21487;&#29992;&#30340; Ubuntu &#20809;&#30424;&#65292;&#37027;&#20040;&#35831;&#25253;&#21578;&#26412;&#38169;&#35823;&#12290;

&#38169;&#35823;&#28040;&#24687;&#26159;&#65306;
'Unable to locate any package files, perhaps this is not a Ubuntu Disc or the wrong architecture?'

method1 and method2   is Same wrong.



Screenshot.png

---

### Post by xjspace on 2008-11-20
8.04 to 8.10,  ¨iso¨ upgrade Method"    iso local     please help me !

---

### Post by Partyboi2 on 2008-11-20
What is the name of the iso you downloaded?

---

### Post by xjspace on 2008-11-21
download name :ubuntu-8.10-alternate-i386.iso

---

