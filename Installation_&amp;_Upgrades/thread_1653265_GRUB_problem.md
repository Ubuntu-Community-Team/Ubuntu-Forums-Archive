---
title: "GRUB problem"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by Sleven7 on 2010-12-26
I was hoping someone would be able to help me.  
I have been duel booting between Windows on the first HDD and Mint 9 on the second HDD on a HP Compaq Core2 Duo and everything worked like it should.

Windows is on /sda1  with Mint 9 on /sdb1. 

This morning I wanted to install the new Linux Mint Debian on the first HDD next to Windows in /sda2  In installation it ask where I want to install GRUB, I chose /sda.  The Installation went well until it got to configuring the bootloader. At this point in the install, it just kept trying to configure the bootloader, this went on for about 30 minutes before I clicked quit.  I then tried to reinstall with GRUB being installed in /sda2.  It also stalled on trying to configure the bootloader. 

I shut the system down and rebooted. Now instead of the bootloader screen coming up, all I get is a black screen with the prompt GRUB>
I typed in "help" and got a partial list of commands, one of which was "REBOOT".  I was then able to reload the live DVD of LMDE, which I am now using to get to this forum.

I would normally go to the Mint Forums, but they have been down all day, so I was hoping that someone here at Ubuntu could help me with the GRUB issue.

Any suggestions?

---

### Post by oldfred on 2010-12-26
Did you try booting the other drive?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Sleven7 on 2010-12-26
oldfred, thank you for trying to help me with this.  I downloaded the script and executed it.  There was alot of output in the terminal, but I can not find the RESULTS.txt file anywhere.  The script was located in /home/mint/Downloads/  I then used the search in the File Browser to try and locate RESULTS.txt and it could not find it either.  I am using the live DVD of LMDE if that helps.  Any idea where to look for the file?

---

### Post by wilee-nilee on 2010-12-26
> **Sleven7 said:**
> oldfred, thank you for trying to help me with this.  I downloaded the script and executed it.  There was alot of output in the terminal, but I can not find the RESULTS.txt file anywhere.  The script was located in /home/mint/Downloads/  I then used the search in the File Browser to try and locate RESULTS.txt and it could not find it either.  I am using the live DVD of LMDE if that helps.  Any idea where to look for the file?

The file will be where the script is, downloads. If not drag the script to the desktop and run this.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by oldfred on 2010-12-26
On my system, the results.txt defaults to /home as the Download folder that I run is from is a link.

 It should tell you as is runs and at the end say where it saved it to.

---

### Post by Sleven7 on 2010-12-26
I moved the script to the desktop and ran it as you said.  RESULTS.txt is not on the desktop or in any of the path file to the desktop.  I looked on the actual desktop and with the File Browser, can't find it.  This is a sample of what the end of the output from the terminal looks like:

Message from syslogd@mint at Dec 26 18:09:52 ...
 kernel:[  618.726069] Code: c6 20 00 00 00 74 0f 89 e8 b9 02 00 00 00 99 f7 f9 89 04 24 29 c5 83 e6 10 74 0c 89 e8 be 04 00 00 00 99 f7 fe 29 c5 8b 44 24 24 <8b> 4c 83 0c 8d 44 0d 00 39 44 24 04 76 29 8b 74 24 04 31 d2 eb 

Message from syslogd@mint at Dec 26 18:09:52 ...
 kernel:[  618.726101] EIP: [<c108a321>] zone_watermark_ok+0x5c/0x9d SS:ESP 0068:f2bd3e4c

Message from syslogd@mint at Dec 26 18:09:52 ...
 kernel:[  618.726105] CR2: 000000007b4ccdd7


That is what is at the bottom of the terminal screen, any ideas?

---

### Post by wilee-nilee on 2010-12-26
So your saying that with the downloaded script on the desktop, then copying and pasting the command doesn't work?

That command is case sensitive copy and paste it, it is the same command from the bootscript link in my signature.

---

### Post by Sleven7 on 2010-12-26
No, the script seems to be working in the terminal, it just not putting the RESULTS.txt on the desktop, or anywhere I can find it.

---

### Post by wilee-nilee on 2010-12-26
@oldfred just trying to get you set for cleanup.:)

Op does your terminal look like this. Post a screen shot if not of your terminal.
[ATTACH]179397[/ATTACH]

---

### Post by Sleven7 on 2010-12-26
Here are the screen shots of the terminal with just the command and one after hitting enter.  This time it hung up after just four lines of output.  The first time there was 3 to 4 screens worth of output.

Not sure how to paste the screen shot, I'm attaching them

[IMG]file:///home/mint/Desktop/Screenshot.png[/IMG]

---

### Post by wilee-nilee on 2010-12-26
> **Sleven7 said:**
> Here are the screen shots of the terminal with just the command and one after hitting enter.  This time it hung up after just four lines of output.  The first time there was 3 to 4 screens worth of output.

Not sure how to paste the screen shot, I'm attaching them

[IMG]file:///home/mint/Desktop/Screenshot.png[/IMG]

Some-things not working do it from a booted live cd.

---

### Post by Sleven7 on 2010-12-26
I had the thought of copying the script to my home folder on sdb1, mint 9.  I was able to copy it there but do not know how to write the path in the command to tell it to look at that drive.  I tried /sdb1/home/joe/boot_info_script*.sh  but got a file does not exist error.  What is the path to sdb1?

---

### Post by Sleven7 on 2010-12-26
I'm working from a live DVD LMDE, I don't have a copy of a live CD and don't have any blanks to make one.  I could boot with a live DVD of Mint 9 or Mint 10 Gnome based on Ubuntu instead of LMDE.

---

### Post by wilee-nilee on 2010-12-26
I think you have grub in the sda mbr.

The script should run normaly it seems to be caught on sda

boot the linux mint 10 and if gparted is not installed install it in the terminal
sudo apt-get install gparted.

Open gparted then right click on the sda then information to see what it says. Is windows there in a partition like sda1 still?

---

### Post by oldfred on 2010-12-26
wilee-nilee, I was going to post my bootscript but I have 3 drives, many partitions and linked folders so it does not look very standard.

If script cannot open partitions, that probably says there are errors. I have had errors on my XP NTFS prevent opening. 

If sda1 is a NTFS partition I would suggest running chkdsk. If a linux ext3 or ext4 partition:

From liveCD so everything is unmounted, change sda1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

From windows repair CD:
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Sleven7 on 2010-12-26
Okay, it will take me a little while, I'm burning a live DVD of Mint 10 Gnome, the one based on Ubuntu. 

Yes, I do believe I over wrote the MBR with GRUB.  In the installation it ask where to put the bootloader and I thought it was supposed to go on sda, that was my selection, live and learn I suppose.  Thank you for all the help, I should be back within 20-30 minutes, if not sooner.

---

### Post by Sleven7 on 2010-12-26
I just had another thought.  I'm not that particularly attached to Windows, haven't even booted it up in months. Do you think if I were to reinstall LMDE and use the entire HDD, would that correct the MBR on sda?  If so, where should I install the bootloader when prompted?

---

### Post by wilee-nilee on 2010-12-26
> **oldfred said:**
> wilee-nilee, I was going to post my bootscript but I have 3 drives, many partitions and linked folders so it does not look very standard.

If script cannot open partitions, that probably says there are errors. I have had errors on my XP NTFS prevent opening. 

If sda1 is a NTFS partition I would suggest running chkdsk. If a linux ext3 or ext4 partition:

From liveCD so everything is unmounted, change sda1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

From windows repair CD:
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

This is what I was thinking.;)

---

### Post by oldfred on 2010-12-26
If you only have one system and one drive you always install the boot loader to sda or the drive not a partition like sda1 or sda2. 

If you have multiple systems you have to decide which system will be primary and have its boot loader in the drive's MBR. Computers only boot from BIOS, to MBR and the code in the MBR then continues the boot. Each drive only has one MBR. Grub2 is really good at finding other operation systems, so I usually recommend using it as the primary boot.

---

### Post by Sleven7 on 2010-12-26
If I want to install LMDE using the entire sda and have Mint 9 on sdb, during the installation of LMDE on sda, where do I install the boot loader?  sda or sda1?

---

### Post by wilee-nilee on 2010-12-26
> **Sleven7 said:**
> If I want to install LMDE using the entire sda and have Mint 9 on sdb, during the installation of LMDE on sda, where do I install the boot loader?  sda or sda1?

Is lmde grub-legacy or grub2, grub generaly goes to the hd no numbers.

If lmde is grub legacy and linuxmint 9 is grub2 then I hope you know what our doing.

---

### Post by Sleven7 on 2010-12-26
I'm not absolutely sure on either account.  I installed Mint 9 months ago, and just downloaded the ISO of LMDE today.  I can tell you that when I boot the system the prompt that comes up on the screen says GRUB> not GRUB2> if that is any indication, which was installed by the LMDE.  And no, I have no idea what I'm doing, lol, other than messing up a system that worked just fine yesterday, thats why I'm here asking questions, :)

---

### Post by wilee-nilee on 2010-12-26
> **Sleven7 said:**
> I'm not absolutely sure on either account.  I installed Mint 9 months ago, and just downloaded the ISO of LMDE today.  I can tell you that when I boot the system the prompt that comes up on the screen says GRUB> not GRUB2> if that is any indication, which was installed by the LMDE.  And no, I have no idea what I'm doing, lol, other than messing up a system that worked just fine yesterday, thats why I'm here asking questions, :)

It happens you wont see grub2 displayed.

I think it might be helpful fir you to be on the right track if you just want to wipe the windows which may be fixable.

Linux mint whether LMDE ot linuxmint 9 0r 10 is all debian based you might as well just run Ubuntu it uses debian packages.

The only real difference with mint in general is it comes with less repos and the medibuntu the repo for cd/dvd.
codecs already. linux 10 i have installed a little lighter build in general.

It sounds more like you want these for a particular reason but like most of us the reasoning might be flawed, lol.:)

So what is your final goal really, what is it that you really want?

---

### Post by Sleven7 on 2010-12-26
My goal this morning was to install LMDE next to Windows and then bench test LMDE against Mint 9 to see which one ran better( faster).  Cgroups 4 lines of code replacing 200 line is touted to make it run faster.  Also LMDE is a rolling distro. LMDE  constantly receives updates. Its ISO images are updated now and   then  but users do not require to re-install it on their systems.  That was a plus also, not having to upgrade every 6 month. I had no end use intentions other than those.

---

### Post by wilee-nilee on 2010-12-26
> **Sleven7 said:**
> My goal this morning was to install LMDE next to Windows and then bench test LMDE against Mint 9 to see which one ran better( faster).  Cgroups 4 lines of code replacing 200 line is touted to make it run faster.  Also LMDE is a rolling distro. LMDE  constantly receives updates. Its ISO images are updated now and   then  but users do not require to re-install it on their systems.  That was a plus also, not having to upgrade every 6 month. I had no end use intentions other than those.

The only thing I'm noticing here is that we are on 24 posts now without anything really happening, this makes me wonder if your wants exceed your ability at this time.

Without being able to see your set up with say screen shots of gparted or the actual bootscript, which doesn't seem to want to run it is difficult to help to be honest.

If you have nothing to loose on the sda HD install one of the mints to it and have sda being read first in the bios.

If you had problems with grub loading to begin with and you put it in sda2 that was a mistake grub goes to the MBR sda.

---

### Post by wilee-nilee on 2010-12-26
So out of curiosity I downloaded the 32 bit LMDE and am installing it in a virtual.

I have LinuxMint 10 installed on my computer it upgrades to grub2 as part of the install. LMDE is marked as LinuxMint 10, but it a larger download a dvd size of 985MIb. Just trying to figure this out to help you if needed.

---

### Post by Sleven7 on 2010-12-26
wilee-nilee and oldfred, thank you so much for all the help.  After chatting with some folks on an irc channel for Mint support, found the channel while looking for an answer, I'm going to install Mint 10 Gnome on sda to correct the problem.  The popular opinion was that LMDE has some serious issues with installation, and how I had it configured was correct, it just doesn't work right yet on many systems. Thanks again for all the assistance.

---

### Post by wilee-nilee on 2010-12-26
> **Sleven7 said:**
> wilee-nilee and oldfred, thank you so much for all the help.  After chatting with some folks on an irc channel for Mint support, found the channel while looking for an answer, I'm going to install Mint 10 Gnome on sda to correct the problem.  The popular opinion was that LMDE has some serious issues with installation, and how I had it configured was correct, it just doesn't work right yet on many systems. Thanks again for all the assistance.

Linux 10 installs nicely, that should be a stable install.

---

### Post by Sleven7 on 2010-12-27
Just wanted to let you know.  I was able to install Mint 10 Gnome next to LMDE on sda and the install corrected the boot loader issue almost perfect.  I can now boot Mint 9, Mint 10, and LMDE with no problems.  Windows some how got lost in the shuffle, but I'm not going to lose any sleep over that.  Thanks again guys for all the help.

---

