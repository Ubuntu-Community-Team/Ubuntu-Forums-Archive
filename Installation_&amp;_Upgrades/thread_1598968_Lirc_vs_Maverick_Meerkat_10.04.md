---
title: "Lirc vs Maverick Meerkat 10.04"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Kheops_74 on 2010-10-17
It does this at each update . I upgrade to 10.10 and lirc is not working anymore. In 10.04, i was able to get lirc working using lirc_zilog. zilog is not loaded anymore. If i try to compile, i got error.

My question:
Am i the only one with problem with lirc and Maverick Lucid?
Must i continue to use lirc_zilog?
Does a new lirc_zilog.diff exist for lirc 0.8.7?

Thanks

K

---

### Post by Kheops_74 on 2010-10-18
Looks like lirc_zilog is the solution again. Where i can find the new .diff? is the question.


[http://wilsonet.com/?page_id=95](http://wilsonet.com/?page_id=95)
> So certain Hauppauge WinTV PVR-150 cards that have a Zilog z8 IR chip on them used to work with lirc_i2c stopped working, as the lirc_i2c driver doesn&#8217;t claim to support an i2c device id of ir_rx_z8f0811_haup. However, the lirc_zilog driver *does* claim to support ir_rx_z8f0811_haup. So the answer to this problem is for people to use lirc_zilog instead (after acquiring the requisite &#8220;firmware&#8221; blob that it needs &#8212; google knows where to find it, its also covered somewhere on this site in a blog posting on the hdpvr&#8217;s IR part). Note that lirc_i2c is likely to disappear entirely in the relatively near future, supplanted entirely by ir-kbd-i2c, which is now ported to ir-core, and its input layer event device can be snarfed for keypress data. It even works with ir_rx_z8f0811_haup devices (lirc_i2c *could* be made to support them as well, but I see no point in it, when its going away anyway).

---

### Post by Kheops_74 on 2010-10-20
No answer. Does it means i'm the only one with a pvr150 and hdpvr not working on maverick 10.10?

I tried a lot of things without success. The only thing i don't know how to do is to make lirc_zilog work with the new kernel and the version 0.8.7 of lirc. Sooo sad!


K

---

### Post by Kheops_74 on 2010-10-20
I try the old patch that work on 10.04. Anybody knows what is auto.conf or autoconf.h. These files seem to be missing

Command line:

sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.7
sudo patch -p0 < ~/zilog.diff
> 
patching file lirc-modules-source.conf
patching file dkms.conf
patching file Makefile
patching file drivers/lirc_zilog/.deps/lirc_zilog.Po
patching file drivers/lirc_zilog/Makefile
patching file drivers/lirc_zilog/lirc_zilog.c
patching file drivers/Makefile
Hunk #1 succeeded at 246 (offset 110 lines).

sudo dpkg-reconfigure lirc-modules-source
> 
Removing all DKMS Modules
Done.
Loading new lirc-0.8.7~pre3 DKMS files...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.7~pre3/build/ for more information.

Excerpt of /var/lib/dkms/lirc/0.8.7~pre3/build/make.log
> make -C drivers SUBDIRS="lirc_zilog"
make[1]: entrant dans le répertoire « /var/lib/dkms/lirc/0.8.7~pre3/build/drivers »
Making all in lirc_zilog
make[2]: entrant dans le répertoire « /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog »
cp ./../lirc_dev/Module*.symvers .
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
	make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog modules \
		KBUILD_VERBOSE=1
make[3]: entrant dans le répertoire « /usr/src/linux-headers-2.6.35-22-generic »
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/.tmp_versions ; rm -f /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog
  gcc -Wp,-MD,/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/.lirc_zilog.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/ -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/../.. -I/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/../.. -I/lib/modules/2.6.35-22-generic/build/include/ -I/lib/modules/2.6.35-22-generic/build/drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_zilog)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_zilog)"  -c -o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/.tmp_lirc_zilog.o /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/lirc_zilog.c
/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/lirc_zilog.c:41: [COLOR="Red"]fatal error: linux/autoconf.h[/COLOR]: Aucun fichier ou dossier de ce type
compilation terminated.
make[4]: *** [/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog/lirc_zilog.o] Erreur 1
make[3]: *** [_module_/var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog] Erreur 2
make[3]: quittant le répertoire « /usr/src/linux-headers-2.6.35-22-generic »
make[2]: *** [lirc_zilog.o] Erreur 2
make[2]: quittant le répertoire « /var/lib/dkms/lirc/0.8.7~pre3/build/drivers/lirc_zilog »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /var/lib/dkms/lirc/0.8.7~pre3/build/drivers »
make: *** [zilog] Erreur 2


---

### Post by Kheops_74 on 2010-10-20
I install linux-source-2.6.35 package and change #include <linux/autoconf.h> to #include </usr/src/linux-headers-2.6.35-22-generic/include/generated/autoconf.h> in the /drivers/lirc_zilog/lirc_zilog.c file.

The command "sudo dpkg-reconfigure lirc-modules-source" works and /dev/lirc0, /dev/lirc1 appear. The remote work.

My last problem is the irsend command. I receive an error

irsend --device=/dev/lircd SEND_ONCE blaster 1
> 
irsend: command failed: SEND_ONCE blaster 1
irsend: hardware does not support sending


I already had this one in the past but i don't remember what it was.

---

### Post by Kheops_74 on 2010-10-20
I get lirc_zilog.c source code from this site [http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=blob_plain;f=drivers/staging/lirc/lirc_zilog.c;h=1b013bf3389927db03696e2fad21479c0252acc9;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=blob_plain;f=drivers/staging/lirc/lirc_zilog.c;h=1b013bf3389927db03696e2fad21479c0252acc9;hb=HEAD) and replace mine. 

I did sudo dpkg-reconfigure lirc-modules-source again and 
sudo rmmod lirc_i2c
sudo rmmod lirc_zilog
sudo rmmod lirc_dev
sudo modprobe lirc_i2c
sudo modprobe lirc_zilog

I modify the hardware.conf and lircd.conf.

The blaster work

---

### Post by Kheops_74 on 2010-10-20
What a mess. Where is the Ubuntu Community when you need them?

---

### Post by gleepwurp on 2010-10-25
Hi Kheops,

glad to know I'm not alone having this issue... THat is primarily the reason I never upgrade the kernel in my mythbox... Everytime is a hassle and I'm afraid to death of messing up everything... Still can't understand how come at release 10.10 we're still not able to get an IR Blaster from a PVR-150, whcih presumably everyone in the mythtv world uses, and still doesn't work out of the box...

I messed up my mythtv box yesterday and I have to re-install everything from scratch (might as well use 10.10)... Everything went smoothly, except the IR Blaster... 

Glad I found your post, I'll be validating if it works for me...

Merci!

Gleepwurp.

---

### Post by gleepwurp on 2010-10-25
Confirmed,

works well for me too!

Thanks again!

Gleepwurp.

---

### Post by tunzo on 2010-10-25
Kehops thanks for figuring this out!  I have been fighting with this problem for a week or more now.  I was able to work through your process over the weekend and was getting some functionality out of the IR blaster.  However, my Hauppauge remote was sending (or the HDPVR was interpreting) 3 signals per button push.  I believe that this lead to the eventual crash of Myth or the HDPVR.  Upon recovery from the crash, I no longer have blasting capability.  I tried to repeat your process this evening and I am now getting:

FATAL: Error inserting lirc_zilog (/lib/modules/2.6.35-22-generic/kernel/drivers/staging/lirc/lirc_zilog.ko): Invalid argument

As I am quite new to Myth and extremely new to LIRC, I am unsure of what I am doing wrong.  As I understand it, the steps you followed are:

1. install lirc-modules-source
2. apply patch zilog.diff to /usr/src/lirc-0.8.7~pre3
3. replace /usr/src/lirc-0.8.7~pre3/drivers/lirc_zilog/lirc_zilog.c with the version that you linked in your earlier post
4. dpkg-reconfigure lirc-modules-source

At this point, lsmod does not show the new modules loaded.  I modprobe them and get the error that I stated above.  Something that may impact this is that during the dpkg-reconfigure, I get this message:

lirc_zilog.ko:
Running module version sanity check.

Good news! Module version  for lirc_zilog.ko
exactly matches what is already found in kernel 2.6.35-22-generic.
DKMS will not replace this module.
You may override by specifying --force.

depmod....

DKMS: install Completed.


Up until my crash this weekend, it seemed to be working fine as I could irsend commands with no issue from the command line.  within minutes of trying to use the remote in Myth, I had the crash and now I am at a loss as to why it isn't working.  Any suggestions that you or anyone else may have would be greatly appreciated!  Thanks!  

I am very new to these forums so if I am doing something wrong or I need to provide more information please let me know!

For reference my system is:
Ubuntu 10.10
2.6.35-22-generic
MythTV 0.23
Hauppauge HDPVR with firmware obtained 2 weeks ago from website installed
Hauppauge HDPVR remote
AMD XP 2500+

---

### Post by martygeek on 2010-10-26
I just moved over to 10.10 this weekend after having been on Fedora for years. Everything works just fine - except my remote control.  I can't seem to get it working, despite having gone through all I know.

On Fedora, there was a lirc tool called mode2 that let me see the codes in a term. window
just to see if anything was actually getting into the socket. Anything like that on Ubuntu?

This ain't worth going back to the instability of Fedora to get working but it would be nice if I didn't have have to bring down code and compile in a patch. That's not very "linux for humans."

---

### Post by Kheops_74 on 2010-10-26
Tunzo, i have both HDPVR and PVR150. I use the blaster and the remote of the pvr150. I don't have the problem with the multiple signal. In my research i saw a bug related to hdpvr that looks like this but i don't remember where.

For the message. maybe you can uninstall the lirc_source and remove the directory in /usr/src/lirc... (it's important). After this reboot and reinstall everything. It works for me in version 10.04.

Let me know if it works.

K

---

### Post by tunzo on 2010-10-26
Kehops - thanks for replying.  I will give it a try this evening.  I am at work right now so I can't get to it at the moment
 
thanks

---

### Post by tunzo on 2010-10-26
Kehops:

I removed the lirc-modules-source package, and then deleted /usr/src/lirc... right after that.  before i rebooted the machine, it did an lsmod and noticed that there were a bunch of lirc_ modules loaded at the same time.  i am i correct that these were loaded when i ran dpkg-reconfigure for lirc-modules-source?  anyway, after the machine rebooted, i did another lsmod and saw that now only lirc_dev and lirc_zilog were loaded, and that i now have /dev/lirc0.  

i suspect that this may be due to the fact that i was trying to compile an lirc_zilog module manually as well and perhaps that module was left over and was conflicting with the modules from lirc-modules-source.  i am not certain of this, as i have spent a lot of time trying various things.  if you or anyone else is curious, my method for trying to manually compile was to take the source from the [mythtv hdpvr wiki]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") [here]("http://www.themainlan.com/mythtv/hdpvr-blaster-drivers.tar.gz") and replaced the lirc_zilog.c file with the one you linked in your earlier post. 

at any rate, the problem appears to be resolved for me (for now at least :) ).  a lesson that i have learned is to be a little more methodical in the future in case i stumble upon a solution i can explain how i got there.  thanks for your help on this.

still wrestling with the multiple signals issue, but perhaps that belongs in another thread.  

tunzo

---

### Post by Kheops_74 on 2010-10-26
Nice to hear it works for you too. MythTV without blaster is not very useful. Enjoy your MythTv box until the next major upgrade 11.04 :-)

BTW. This is the thread about the multiple signal that i saw : [http://www.gossamer-threads.com/lists/mythtv/users/420427](http://www.gossamer-threads.com/lists/mythtv/users/420427)

---

### Post by tunzo on 2010-10-26
after searching around i think i have figured out the repeating commands issue.  according to the FAQ at lirc.org, this behavior is typical of remotes.   they apparently send multiple signals when a single button is pressed to  ensure that the signal is not missed.  for anyone who may be having a similar problem:

when i would press a button on my remote it would send multiple signals. for instance, if i pressed the up button then the left button, the irw output would look something like this:

0000000000001795 00 Down Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 00 Left Hauppauge_350

after some searching, it appears that these are "extra" commands being interpreted by lirc.  from what i can tell, however, the output shown above is slightly different "repeated" commands.  irw output for "repeated" commands apparently look like this:

0000000000001794 00 Up Hauppauge_350
0000000000001794 01 Up Hauppauge_350
0000000000001794 02 Up Hauppauge_350
0000000000001794 03 Up Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001795 01 Down Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 01 Left Hauppauge_350

after playing with a few options in lircd.conf, i adjusted the "gap" option for the remote to a higher value. according to lirc.org, the gap option indicates an amount of time after a trailing pulse emitted from a remote. it was set to 114605 and i changed it to 200000.  this caused the extra commands sent by the remote to be interpreted as "repeated" commands now instead of extra commands (notice the 2nd column in the output).  

at this point, there is another option that can be set in lircd.conf called suppress_repeat <x>.  it essentially causes lirc to ignore x repeats of a command.   in my lircd.conf file under the section for this remote, i added:

suppress_repeat 3

now, my output for irw looks like:

0000000000001794 00 Up Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000000001781 00 1 Hauppauge_350
0000000000001782 00 2 Hauppauge_350

the issue seems to be resolved

---

### Post by phroman on 2010-10-28
Hi Tunzo, did your HD PVR work out of the box?  I can't get mine working at all.  Did you do anything special to configure it?  Thanks for any help.

---

### Post by phroman on 2010-10-28
Any idea where you may have seen that bug?  I can't get my hdpvr working..

---

### Post by tunzo on 2010-10-29
hi phroman.  i actually installed the latest firmware into the hdpvr before i ever tried it.  instructions for how to do that can be found on the hdpvr mythtv wiki.  

recently, i installed a fresh 10.04 ubuntu, and before i even installed mythtv, the hdpvr was auto-detected and the module was loaded.  

what issues are you having?

---

### Post by Ghosty.be on 2010-11-01
ok to summarize:

*you need the zilog.diff patch from 10.04 in your home directory [http://ubuntuforums.org/showthread.php?t=1294825&highlight=zilog+lirc&page=7](http://ubuntuforums.org/showthread.php?t=1294825&highlight=zilog+lirc&page=7)
*you need the new lirc_zilog.c in your home directory from [http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=blob_plain;f=drivers/staging/lirc/lirc_zilog.c;h=1b013bf3389927db03696e2fad21479c0252acc9;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=blob_plain;f=drivers/staging/lirc/lirc_zilog.c;h=1b013bf3389927db03696e2fad21479c0252acc9;hb=HEAD)
*you need the binary blob haup-ir-blaster.bin in your home directory from: [http://wilsonet.com/?p=40](http://wilsonet.com/?p=40) (direct link: [http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin) ) 

and run:
sudo apt-get install lirc-modules-source
cd /usr/src/lirc-*/
sudo patch -p0 < ~/zilog.diff
sudo cp ~/lirc_zilog.c drivers/lirc_zilog
sudo dpkg-reconfigure lirc-modules-source
sudo cp ~/haup-ir-blaster.bin /lib/firmware

sudo rmmod lirc_i2c
sudo rmmod lirc_dev
sudo modprobe lirc_zilog

now you should see as output for: lsmod | grep lirc
lirc_i2c                7433  0 
lirc_zilog             15952  0 
lirc_dev               12140  2 lirc_i2c,lirc_zilog

and for: ls /dev/lirc*
/dev/lirc0  /dev/lirc1  /dev/lircd

now restart lircd (and make sure it's configured for a hauppage remote)
sudo service lirc restart

and then run: irw
press some buttons on the remote and this should show something on the terminal.

possible errors: 
*if modprobe lirc_zilog shows "killed" it means you forgot to copy the binary blob.
*if you do not see any devices like /dev/lirc0 or /dev/lirc1 the driver is not working. 

Thx to everyone in this thread ... now to do something useful with this ;)

For reference: 
Hauppage pvr-150 silver remote working under Ubuntu 10.10 x86_64

---

### Post by tzoom84 on 2010-11-08
Hey first I just wanted to thank all of you for making the initial install process so seamless. I was able to run through all the commands listed in Ghosty.be's posts. But when I try to call "irsend" to my blaster, I get an error:
"irsend: transmission failed"

I tried all variants of calling irsend:
```
sudo irsend SEND_ONCE hauppauge_pvr150 POWER
sudo irsend SEND_START hauppauge_pvr150 POWER
sudo irsend --device=/dev/lirc0 SEND_ONCE hauppauge_pvr150 POWER
sudo irsend --device=/dev/lirc1 SEND_ONCE hauppauge_pvr150 POWER
```

I'm using a PVR-150 with the silver remote.

A "dmesg | grep lirc" indicates I may have problems with my lircd.conf. Which lircd.conf do you all use for your PVR-150?

(Note: I first was using the default which pointed to /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge. But when that didn't work, I tried one found at [http://www.pjd.nu/lirc/lircd_pvr150.conf](http://www.pjd.nu/lirc/lircd_pvr150.conf)

Thanks!

---

### Post by tunzo on 2010-11-08
Hi tzoom.  Its been a few weeks since i have messed with anything Myth - ive been working on some other things.  If memory serves me, though, i think I followed the [MythTV HDPVR Wiki]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") for setting up hardware.conf and lircd.conf.  If you look near the bottom of the page, you will see some instructions.  

my (loose) understanding of those files is that hardware.conf lets you attach names to your /dev/lirc's tells what drivers they use, etc.  lircd.conf defines how those devices behave - it defines what signals are sent with what commands.  

It is obviously important to make sure that your name of your sending device matches the name of one of the devices defined in lircd.conf.   i know i got tripped up with the names of things when i was trying to configure it.  

also, whenever you make changes to hardware.conf or lircd.conf, i believe you need to restart the lirc dameon:

sudo /etc/init.d/lircd restart

also, while i don't think this should make a difference, i never needed to use sudo to use irsend.  sorry i can't be of more help.  my understanding of all of this is not very extensive.  hopefully if i am leading you astray, someone will correct me.

---

### Post by tomj.runner on 2010-12-24
Hi all, 

I followed everything in this thread or checked in various others, still no success in making the IR blaster work.
I'm using Marverick 10.10 with a Hauppauge HD-PVR on a Zotac ION computer

So I followed [Ghosty.be]("http://ubuntuforums.org/member.php?u=210244") waltkthrough without issue. Then*

First difference
lsmod | grep lirc returns
lirc_zilog             15952  0 
lirc_dev               12140  1 lirc_zilog

nothing related lot lirc_i2c, which will appear only if I do sudo modprobe lirc_i2c.

Second difference and I fear the issue might be coming from here
ls /dev/lirc* returns /dev/lircd only.
no /dev/lirc0 or /dev/lirc1 (which means no device loading no ?)

dmesg |grep lirc
[   13.656876] lirc_dev: IR Remote Control driver registered, major 61 
[   13.664780] lirc_zilog: Zilog/Hauppauge IR driver initializing
[   13.669597] lirc_zilog: initialization complete
So no issue on the driver loading.

 sudo irsend LIST "" "" returns
irsend: Hauppauge
irsend: hauppauge_pvr
irsend: Hauppauge_350
irsend: Hauppauge_WinTV_Nexus-S
irsend: Hauppauge
irsend: Hauppauge_MVP

The Hauppauge works well, with compiled drivers coming from V4L (linuxtv.org).

But it seems nothing is send to the blaster (no blinking light)
irsend SEND_ONCE Hauppauge 0_1_KEY_POWER
irsend SEND_ONCE Hauppauge_MVP 0_1_KEY_POWER
irsend SEND_ONCE hauppauge_pvr 0_1_KEY_POWER
returns #unknown command"

sudo irsend SEND_ONCE hauppauge_pvr POWER returns nothing.


Any idea of what might be wrong ?

---

### Post by bml137 on 2011-01-21
You need to patch the 'hdpvr' kernel module for the 'lirc_zilog' kernel module to recognize the HDPVR IR receiver and/or transmitter.

---

### Post by Chewiesw on 2011-04-03
Ok, I am in the final stages of installing a new 10.10 box and I have left the lirc config for last as it seems it is the most irritating component. Maybe I should have tackled it first ! I  have driver issue that I am not sure how to solve. I have tried to follow this thread and other but I still can’t get the remote or blaster to work

```
andrew@DVRBOX:~$  ls /dev/lirc*
/dev/lircd
andrew@DVRBOX:~$ lsmod | grep lirc
lirc_zilog             13704  0 
lirc_mceusb            13068  0 
lirc_dev                9510  2 lirc_zilog,lirc_mceusb
andrew@DVRBOX:~$ 
```

Hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

---

### Post by Dave M G on 2011-05-09
Has the system changed in 11.04?

I followed the instructions and everything seemed to go fine until the very last step, when I got this error:

```
$ sudo modprobe lirc_zilog
FATAL: Error inserting lirc_zilog (/lib/modules/2.6.38-9-generic/kernel/drivers/staging/lirc/lirc_zilog.ko): Invalid argument
```

Is there something else I need to do?

Thanks for any advice.

---

### Post by Kheops_74 on 2011-05-10
Do you tried removed the lirc-modules-source package, and then deleted /usr/src/lirc

After you can start the procedure again described in this tread.

---

### Post by Dave M G on 2011-05-10
I think things have changed.

Something wasn't going right when downloading lirc-modules source, so I went into Synaptic to check it, and it said:

```
This package can be safely removed as the in-kernel modules supercede it.
```

So I ran an update, rebooted, and my remote works!

Could it be that the lirc drivers are now built in so all this crazy configuration is not needed anymore?

---

### Post by bsntech on 2011-06-20
> **Dave M G said:**
> I think things have changed.

Something wasn't going right when downloading lirc-modules source, so I went into Synaptic to check it, and it said:

```
This package can be safely removed as the in-kernel modules supercede it.
```

So I ran an update, rebooted, and my remote works!

Could it be that the lirc drivers are now built in so all this crazy configuration is not needed anymore?

A bit of an old threat here, but I believe you are on to something.  Anytime I did an upgrade of a release or kernel, I had to re-patch the lirc-modules-source and the run a reconfigure on it.

Now with LIRC 0.8.7 and 11.04 installed, the Hauppauge HVR 1600 remote I have works just fine.  I upgraded to 11.04 and then simply ran 'sudo dpkg-reconfigure lirc-modules-source' and all is well.

In the /etc/lirc/hardware.conf file, my line looks like this:

REMOTE_MODULES="lirc_dev lirc_zilog" 

Working just fine.  Nice to see that the lirc_zilog appears to be working fine in the lirc-modules-source.

Brian S.
[Small Business Website Design]("http://www.bsntech.com")

---

### Post by IndieRockSteve on 2011-12-05
has anyone tried this on 10.04 lately? the patch doesn't apply cleanly any more and I can't find the linked to version of the lirc_zilog.c file by Ghosty.be.

---

