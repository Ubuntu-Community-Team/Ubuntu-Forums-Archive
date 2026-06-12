---
title: "Dummynet ipfw install"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by vweissman on 2009-11-25
Hi all,

I am new to Ubuntu and Linux, I installed the Ubuntu 9.1 release since for my project I need to use Dummynet that is a part of the ipfw, it is a part of FreeBSD and in this page: 

[http://manpages.ubuntu.com/manpages/karmic/man4/dummynet.4freebsd.html](http://manpages.ubuntu.com/manpages/karmic/man4/dummynet.4freebsd.html) 

it says that it is possible to add Dummynet/ipfw to Ubuntu by doing this: 
 To compile **ipfw** into the kernel, place the following option in the kernel
     configuration file:

           **options** **IPFIREWALL**

[FONT=Verdana]Can someone guide me through the needed steps for this task? What files do I need to download and how to compile etc..?

Thank you all in advance.

Val[/FONT]

---

### Post by linxnub on 2010-05-24
I am very new to linux and have recently tried out some different flavors. A few weeks ago I did setup Dummynet on Debian. Although this tut I created for myself may apply to yours or someones install on Ubuntu and Debian.
 
I have not tried this on Ubuntu but you could pick out the information that matters.
 
[FONT=Times New Roman][SIZE=3]Install Debian[/SIZE][/FONT]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Change PC to boot from cdrom in your bios (usually F2 when you first power on will get you to your bios).[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]Select Install from the Menu option for basic core install.[/SIZE][/FONT]
[/LIST][FONT=Times New Roman][SIZE=3]-or-[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Optionally you can choose Advanced Option and then Graphical Auto-Install and answers the prompts when given.[/SIZE][/FONT]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Install the following when listed[/SIZE][/FONT]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Standard System[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]Web Server (optional)[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]DNS Server (optional)[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]File Server (optional)[/SIZE][/FONT]
[/LIST]
[*][FONT=Times New Roman][SIZE=3]Rest of the prompts are self explanatory - root password, user name and user password…etc.[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]Finally the system reboots and you end up at a User login prompt. Once signed in you are at the User Terminal.[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]OS installation complete.[/SIZE][/FONT]
[/LIST][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Debian configuration[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Debian must be configured with a few apts so that you can install Dummynet. You will need to create your own executable and kernel module using your kernel headers. Without them you will get a constant errors when you try to use insmod or modprobe.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Create a new directory to house your ipfw install. I created a directory called ipfw3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[LIST]
[*][FONT=Times New Roman][SIZE=3]First thing I would do is create a snapshot of your newly installed system. [/SIZE][/FONT]
[LIST]
[*][FONT=Times New Roman][SIZE=3]List modules installed and save to file (Optional)[/SIZE][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][SIZE=3]#lsmod > /ipfw3/mymod.txt [/SIZE][/FONT]
[LIST]
[LIST]
[*][FONT=Times New Roman][SIZE=3]List hard drives and partitions. (Optional)[/SIZE][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][SIZE=3]#fdisk –l > /ipfw3/mystorage.txt[/SIZE][/FONT]
[LIST]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Whatever else you wish to save (Optional)[/SIZE][/FONT]
[/LIST]
[*][FONT=Times New Roman][SIZE=3]I would log into root at this point, there are few packages that need to be installed.[/SIZE][/FONT]
[/LIST][FONT=Times New Roman][SIZE=3]apt-get show pkgname – gives a description of a package[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]apt-get stats pkgname – give size information[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]apt-get search pkgname or if you only know part of the pkgname you could use pkg*[/SIZE][/FONT]
[LIST]
[LIST]
[*][FONT=Times New Roman][SIZE=3]As always update the packages before you do anything.[/SIZE][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][SIZE=3]#apt-get update[/SIZE][/FONT]
[LIST]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Add the libncurses development package[/SIZE][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][SIZE=3]#apt-get install libncurses5-dev[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]subsequently the following packages will also be installed automatically:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1.[/SIZE]      [SIZE=3]binutils[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2.[/SIZE]      [SIZE=3]gcc[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3.[/SIZE]      [SIZE=3]gcc-4.3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]4.[/SIZE]      [SIZE=3]libc6-dev[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]5.[/SIZE]      [SIZE=3]libgomp1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]6.[/SIZE]      [SIZE=3]linux-libc-dev[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]suggested packages are listed and you will need to install “make” next.[/SIZE][/FONT]
[LIST]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Add the make package[/SIZE][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][SIZE=3]#apt-get install make[/SIZE][/FONT]
[LIST]
[LIST]
[*][FONT=Times New Roman][SIZE=3]Add the headers for your system which will be needed when creating your ipfw_mod.ko kernel file.[/SIZE][/FONT]
[/LIST]
[/LIST][FONT=Times New Roman][SIZE=3]#apt-get install linux-headers-$(uname –r)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]subsequently the following packages will also be installed.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1.[/SIZE]      [SIZE=3]cpp-4.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2.[/SIZE]      [SIZE=3]gcc-4.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3.[/SIZE]      [SIZE=3]gcc-4.1base[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]4.[/SIZE]      [SIZE=3]linux-headers-2.6.26-2-common (2.6.26-2 can change based on your kernel)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]5.[/SIZE]      [SIZE=3]liunx-kbuild-2.6.26 (2.6.26 can change based on your kernel)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]6.[/SIZE]      [SIZE=3]That is all the configurations needed for Debian to allow the processes for installing Dummynet[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Dummynet Installation[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Without installing the packages as directed above you will not be able to install Dummynet. The version on the website is for the wrong kernel. Just do a modinfo command on the ipfw_mod.ko and you will see the kernel version it was created on. (You probably could download the kernel headers for that module and link the header for that apt, but I feel that this is not the best way.)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]            [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1.[/SIZE]      [SIZE=3]Now let’s get to business…Copy, move, download the source code to your /tmp directory.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Example: While in your /tmp directory initiate the following command[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#wget [http://info.iet.unipi.it/~luigi/dummynet/20100319-ipfw3.tgz](http://info.iet.unipi.it/~luigi/dummynet/20100319-ipfw3.tgz)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2.[/SIZE]      [SIZE=3]The file is a compressed in a .tgz format and you will have to expand it.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]While in the /tmp directory initiate the following command and a new directory called /tmp/ipfw3/ will be created.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#tar xvzf 20100319-ipfw3.tgz[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3.[/SIZE]      [SIZE=3]Navigate to the /tmp/ipfw3 directory and initiate the “make” command.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#make[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]4.[/SIZE]      [SIZE=3]2 files were created and need to be copied to another location[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]a.[/SIZE]       [SIZE=3]ipfw executable was created in the directory /tmp/ipfw3/ipfw/ and [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]you should copy it to the /ipfw3 directory created earlier in this tut.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#cp /tmp/ipfw3/ipfw/ipfw /ipfw3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]b.[/SIZE]      [SIZE=3]ipfw_mod.ko kernel module was created in the /tmp/ipfw3/dummynet2/ directory and should be copied to the /ifpw3 directory.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]c.[/SIZE]       [SIZE=3]#cp /tmp/ipfw3/dummynet2/ipfw_mod.ko /ipfw3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]5.[/SIZE]      [SIZE=3]Install the Dummynet files[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]a.[/SIZE]       [SIZE=3]Copy the ipfw executable file to the /usr/local/sbin[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# cp /ipfw3/ipfw /usr/local/sbin[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]b.[/SIZE]      [SIZE=3]Copy the ipfw_mod.ko to its destination by initiating the following command[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#cp /ipfw3/ipfw_mod.ko /lib/modules/`uname –r`[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]c.[/SIZE]       [SIZE=3]Run depmod to update the modules.dep file so that you can use modprobe.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#depmod[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]d.[/SIZE]      [SIZE=3]Now you can use modprobe to install the kernel module[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#modprobe ipfw_mod[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]You can at this point lsmod to view the installed modules and to see if the module is working, type the following:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#ipfw list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Which displays:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]65535 allow ip from any to any[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]e.[/SIZE]       [SIZE=3]You will loose the module if you reboot at this time, so to make the module load during boot you need to edit the etc/modules file with a text editor. Add **ipfw_mod** as the last entry in the file, save the file and you can now reboot and Dummynet is ready for rules to be added.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]f.[/SIZE]        [SIZE=3]To restart the system and test the install initiate the following command:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#shutdown –r[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
 There definitely maybe an easier way to accomplish but since I am new to the linux world this is all that I could do to get dummynet working on debian
 
Maybe someone can figure out how to maintain the rule sets after a reboot is done?

---

### Post by burnbrighter on 2011-06-18
Validated as working in 9.10 (Karmic Koala) only!  Later versions have issues.

---

### Post by YosemiteSam on 2012-01-31
Worked for 9.04 Jaunty Jackalope.

---

### Post by Pfunk1410 on 2013-02-08
Worked on Ubuntu 12.04.1 LTS (Precise Pangolin).
I downloaded IPFW source from [http://info.iet.unipi.it/~luigi/doc/20120812-ipfw3.tgz](http://info.iet.unipi.it/~luigi/doc/20120812-ipfw3.tgz)

---

### Post by oldos2er on 2013-02-08
Old thread closed.

---

