---
title: "how to get my windows partition to boot again"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by northwestuntu on 2011-08-25
i wanted to dual boot lubuntu and my existing windows xp.  i installed lubuntu 8.10 and everything was fine at boot.  i could boot in to either then i upgraded lubuntu to 9.04 and windows was gone from grub?  

can i delete my lubuntu partition and windows will boot again?

---

### Post by oldfred on 2011-08-26
No.

Ubuntu has installed a grub legacy boot loader to the MBR. Grub legacy was not very good at adding windows boot stanzas to menu.lst. One of the real advantages of the newer Ubuntus (9.10 and after) is grub2's os-prober that finds windows almost every time and most other systems and lets you boot them.

If you just want windows you have to install a windows boot loader or lilo from Ubuntu. Lilo works just like windows in the MBR and will boot Windows.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

If you want a menu.lst stanza to add for your Ubuntu, although it is probably time to upate to 10.04 LTS or 11.04. Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by northwestuntu on 2011-08-26
thanks for the suggestions ill give them a shot

---

### Post by madjr on 2011-08-26
yea installing a newer version could solve the prob

---

### Post by Cope57 on 2011-08-26
Would it not be easier to install os-prober and update grub to get windows to show in the grub menu?

sudo apt-get install os-prober
sudo update-grub

I works for grub 2, but I do not know what version Lubuntu 9.04 uses.

---

### Post by northwestuntu on 2011-08-26
im sorry guys i got my versions mixed up.  windows was on the pc. i installed lubuntu 10.10 everything was fine...could see both lubuntu and windows xp.

then i updated lubuntu to version 11.04 then windows was not on boot screen anymore.  the partition is there, but can't get it back on the boot.  i tried to do a grub update to add it, but didn't work.

---

### Post by northwestuntu on 2011-08-26
> **Cope57 said:**
> Would it not be easier to install os-prober and update grub to get windows to show in the grub menu?

sudo apt-get install os-prober
sudo update-grub

I works for grub 2, but I do not know what version Lubuntu 9.04 uses.

i didnt try the os-prober but did do the update-grub and didnt work.  thats something i will try.

---

### Post by northwestuntu on 2011-08-26
also could i delete the lubuntu partition and install lubuntu again.  would that re write the MBR? and maybe pickup windows

---

### Post by garvinrick4 on 2011-08-26
[COLOR=Red]###EDIT, I have just noticed you are in 9.04 with legacy grub, sorry, go with oldfred's post. [/COLOR]My code is for grub2 9.10 and up. Why are you using version not supported, download 11.04 Lubuntu is nice.


> also could i delete the lubuntu partition and install lubuntu again.  would that re write the MBR? and maybe pickup windowsYes, but would be much easier to install grub2 to mbr with a couple of lines of code.
What is output of 
```
sudo fdisk -l
``` (lower case L)

#As long as you have a good install of Windows and lubuntu will be a breeze.
Best way is to actually do the boot_info_script I believe was mentioned.
But if you want to give the output of fdisk will give you code to install grub2 and update
in your install cd (using Try Ubuntu) called a live CD:

##If you can boot into lubuntu now Just do this in a terminal:
```
sudo grub-install /dev/sda
``````
sudo update-grub
``````
grep menuentry /boot/grub/grub.cfg
```The first 2 lines of code put grub in mbr again the 3rd shows you all menuentrys now.
Hopefully Windows is in there now.

---

### Post by Ibidem on 2011-08-26
I'd suggest trying the aforementioned method again, with a couple details done beforehand.
First, make sure that your Windows drive is mounted (ie, you can read files from it)
Second, make sure that os-prober is installed (sudo apt-get install os-prober)
Third, "sudo update-grub"
If you don't do both 1 & 2, then Grub won't recognize Windows.

DO NOT try to just delete *buntu; you will get "Errror 15" or some such issue, and will not have a bootable computer at all.  There must be a bootloader installed in the MBR to boot; Windows uses its own, while Linux uses a different one (grub)
The Windows MBR detects the "active" partition to boot; Grub uses a configuration file, stored on the Ubuntu partition.  You will need to re-write the MBR to boot without Lubuntu.
Some recommendations that come to mind are grub4dos/the ultimate boot CD (UBCD), and ms-sys.  the Ultimate Boot CD is probably the best bet.

---

### Post by northwestuntu on 2011-08-26
thanks for the details guys.  this computer is at a friends house so ill have to wait til tomorrow to try it out.  ill let ya know how it works.

---

### Post by Quackers on 2011-08-26
Lubuntu is known to fail to install os-prober sometimes. If os-prober is not installed then no other operating systems will be found.
Check to see if it is installed using synaptic package manager.
If it isn't installed install it then run sudo update-grub in the terminal.

---

### Post by garvinrick4 on 2011-08-26
Hello Quackers good to see you around:

You can also run:
```
sudo os-prober
```
If os-prober is installed will run it and see all your other installs.

---

### Post by madjr on 2011-08-26
> **northwestuntu said:**
> also could i delete the lubuntu partition and install lubuntu again.  would that re write the MBR? and maybe pickup windows

yes, you can reinstall if thats easier for u.

if you run into more boot issues, just use boot-repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html](http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html)

---

### Post by northwestuntu on 2011-08-27
> **Quackers said:**
> Lubuntu is known to fail to install os-prober sometimes. If os-prober is not installed then no other operating systems will be found.
Check to see if it is installed using synaptic package manager.
If it isn't installed install it then run sudo update-grub in the terminal.

tried this 1st and worked perfectly.

thanks! :P

---

### Post by Quackers on 2011-08-27
Ah! Very nice :-)

---

