---
title: "can't install on other HDD"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by jimbo10 on 2014-12-26
just tried installing UBUNTU 14.04 (April 2014 release) on my desktop (running an old P4)......on my second HDD ("f" drive, not "c" drive.....both masters)

no go! :(

error msg said some-thing like: "need to create boot partition"  :confused:

what do ii need to do........to get UBUNTU running on my "f" drive......?
(am running Vista Ultimate on "c" drive)

thnx!

much appreciated

---

### Post by Bucky Ball on 2014-12-26
Welcome. When you get to the partitioning section of the install choose 'Something Else' and create a partition with the mountpoint / and another with the mountpoint /swap (2Gb). You can create others like /home for your data if you want (or named anything you want). The three mountpoints I mention are default options in the partitioning section when you hit 'Something Else'. Install grub to sda (you will understand when you get there, but any problems, just ask). 

You give no info about how you are attempting to install so hard to be specific about what you may or may not be doing wrong. Good luck. ;)

A bit off-topic, but with a P4, unsure how a full Ubuntu install will run. How much RAM do you have? Any less than 2Gb will probably not be a very satisfactory experience. You might be better with Xubuntu or Lubuntu.

---

### Post by jimbo10 on 2014-12-26
thanks for that.....
uhmm.....k......i'll have to go and re-read my LINUX "bible" vis á vis "sudo" and "mount"...

there is 4gb of RAM....but......i'm currently running 32-bit version of Vista Ultimate.....so....only 3gb is accessed....that's why i was hoping to get the UBUNTU 14.04 going because its 64-bit, eh?

i'm installing from a DVD i got off e-bay.....for $5....!

(will have another 'go' and, if any problems, get back, eh?)

thanks again!

---

### Post by Dreamer Fithp Apprentice on 2014-12-26
Added by edit: You can probably skip this as I doubt I wrote anything the faster typists above didn't cover. This was unanswered when I started slowly pecking away.

More detail is necessary if anyone is to understand exactly what you tried and the context of the error message. The exact message and exactly what steps led to it would be nice. There's more than one way of installing Ubuntu. Refering to the drives as "c:" and "f:" is only valid from within Windows. I'm not just being pedantic - this could be a source of confusion as the installer will use letters also, but probably not the same ones and they'll be parts of longer strings. I believe if it is a SATA or SCSI (I may not have the 2nd acronym quite right) the first drive the bios checks for a bootable partition (which is not necessarily the c: drive - the FIRST drive it checks may not HAVE a bootable partition) is sda, the second is sdb, and so on. If the drives are IDEs they are designated hda, hdb, and so on. The important thing is to be very, very sure, you know which drive is which and where your Windows (or other valuable data) is so you don't wipe it out. Taking careful note of the partition sizes might help. If you install from an installation cd (or thumb drive I presume, though I haven't actually done that) at some point you'll have to tell it where to put the "/", aka "root" partition. This is normally the only partition that is essential. A "boot" partition is normally optional. Could the error message have been more like "must designate a root partition"? That would make more sense to me. If that is it you simply neglected to designate where to put the Ubuntu. If you go through the manual partitioning with the installer, after you tell it what kind of filesystem to expect on each partition, you tell it how (and if) to mount it. That may be the step you skipped. You want the partition where you want the Ubuntu to mount as "/". That will probably be a choice on a drop down menu. You don't HAVE to tell it to mount any other partition automatically, although you CAN, but it MUST mount "/", aka "root".

---

### Post by jimbo10 on 2014-12-26
thanks for that....
one of the HDDs (the current Windows "c" drive) is IDE .....250gb;
the other HDD (currently "f") is SATA.....500gb;

there is nothing on the "f" drive....i deleted every-thing...although it is still 'formatted' as NTFS by Vista......

the "f" drive is where is want to install UBUNTU because my "c" drive is filling up fast and, also, the Vista updates are not installing....and....i couldn't be bothered re-installing it.....

ultimately, if i get UBUNTU up and running properly, i'll ditch the Windows altogether.....and......may oik out the "c" drive any-way.....

oh yeh...i recall it saying "sda" and "sdb".....but....i'm a bit fuzzy abt the actual "error" msg....

will have to re-check....

back to the drawing-board, eh?  :frown:

---

### Post by Bucky Ball on 2014-12-26
As mentioned, when you get to the partitioning section of the Ubuntu install and choose 'Something Else' you will be able to delete the NTFS partition on the sdb (presumably) drive and install Ubuntu. For Ubuntu, you need to use EXT4 filesystem partitions.

@Dreamer Fithp Apprentice: Could you use paragraphs, please. The 'black blob' approach is difficult to read and can cause issues for those with vision problems. Thanks. ;)

---

### Post by fantab on 2014-12-26
Boot Ubuntu Live DVD/USB, 'Try Ubuntu (without installing). open Terminal, run the following command and post its output here:
```
sudo parted -l
sudo fdisk -l
```

On one of my machines I have Windows 32bit and Ubuntu 64 booting harmoniously.

---

### Post by Dreamer Fithp Apprentice on 2014-12-26
> **Bucky Ball said:**
> As mentioned, when you get to the partitioning section of the Ubuntu install and choose 'Something Else' you will be able to delete the NTFS partition . . .  I could possibly be mistaken, and welcome correction if I am, but that shouldn't be strictly necessary if you want to use the whole drive. You can just designate that partition to use ext3 or ext4 for example, then mark it to be mounted as "/" (aka "root", although calling it that can be confusing as you will also be creating a directory NAMED "root" literally, i.e., "/root/"), and check the box to format the partition. That would be the easiest way to do it. Strictly speaking, I'm not sure you even HAVE to reformat. I'm not absolutely certain about Ubuntu, but some 'nixes can live quite happily on an NTFS filesystem. Even if you can do it that way though, I'd strongly reccomend against it. A lot of software and a lot of tutorials assume a native filesystem format and will screw up on an NTFS.

 However you might wish to consider repartitioning that drive before you install, and if you do then you would start as Bucky Ball suggests by deleting the partition. Then divide it into 2 or more partitions, designate 1 of them to be formatted ext4 and mounted as "/", then proceed to install on it. Whether that is desirable depends on how much space you have and how much data you expect to have. Ubuntu itself won't need that much - 30 giB is almost alway way more than enough and I don't think I've ever used more than 15 for any 'buntu. And there is a lot to be said for keeping your data (meaning stuff like your spread sheet modeling global weather, the novel you are writing, your emails, your videos and sound recordings, etc., etc.) on a seperate partition. It makes backing up both your system and your data a whole lot easier IMO, although not everyone agrees.

> **Bucky Ball said:**
>  . . . on the sdb (presumably) drive . . . Probably that's true, as any chance better than 50% is probable. But presumption is dangerous for the reason I mentioned before. Don't presume. Make SURE. Better safe than sorry.

---

### Post by Mark Phelps on 2014-12-26
> what do ii need to do........to get UBUNTU running on my "f" drive......?

Basically, you -- can't!  Why" Because "F" is a drive letter assigned to a Windows filesystem partition -- and not only does Ubuntu NOT use drive letters, it also can't be installed to a Windows filesystem partition.

The details others have provided tells you to use the Something Else option to remove the "F" partition and replace it with Linux filesystem partitions.

---

### Post by grahammechanical on 2014-12-26
May I suggest a method?

1) Disconnect the 250GB IDE drive.
2) Run the Ubuntu installer with only the 500GB SATA drive connected and choose the Erase Disk and Install Ubuntu option.
3) Test the loading of Ubuntu.
4) Make sure that the BIOS has boot priority set to the SATA drive and not the IDE drive.
5) Re-connect the 250GB IDE drive.
6) Load into Ubuntu and open a terminal and run

```
sudo update-grub
```

See if the updating of Grub detects Windows. Reboot and see if you get a boot menu with both Ubuntu and Windows as boot options. Test both operating systems.

Regards.

---

### Post by jimbo10 on 2014-12-30
> **grahammechanical said:**
> May I suggest a method?

1) Disconnect the 250GB IDE drive.
2) Run the Ubuntu installer with only the 500GB SATA drive connected and choose the Erase Disk and Install Ubuntu option.
3) Test the loading of Ubuntu.
4) Make sure that the BIOS has boot priority set to the SATA drive and not the IDE drive.
5) Re-connect the 250GB IDE drive.
6) Load into Ubuntu and open a terminal and run

```
sudo update-grub
```

See if the updating of Grub detects Windows. Reboot and see if you get a boot menu with both Ubuntu and Windows as boot options. Test both operating systems.

Regards.

[FONT=times new roman]
[/FONT][COLOR=#0000ff]thnx for that.....
uh....you know.....ha ha....that's just what the bloke in the local computer shop told me to do.....
problem is....i was too lazy to oik the case off the floor, open it & dis-connect the IDE drive....  [/COLOR]:o[COLOR=#0000ff]
well....i guess i will do it now......
oh.....yeh...one question.....UBUNTU has that "grub" boot-loader already on the CD/DVD, right?

(meant to do all this ....but.......a bit too much on me plate over Xmas, eh?.....hmm....looks like i'll hafta have a 'go' though, eh?)[/COLOR]

cheers!

ps: uh-oh!.....i just realised......the BIOS doesn't differentiate the HDDs.....all it has in "boot priority" is HDD (along with the other options....CD/USB/ZIP &c).....where's that leave me?
pps: guess i could get around that by making the SATA drive the primary master, eh?.....or would it be better to have the SATA drive/IDE drive set up as master/slave?.....or......hmmmm.....would that cause problems vis á vis UBUNTU ?

---

### Post by Bucky Ball on 2014-12-30
Boot from the install media (disk or USB), when you get to the partitioning section of the install, choose 'Something Else' and manually partition. 

[This link ]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352")might help to point you in the right direction and if you have questions, just ask. ;)

---

### Post by jimbo10 on 2014-12-30
> **Bucky Ball said:**
> Boot from the install media (disk or USB), when you get to the partitioning section of the install, choose 'Something Else' and manually partition. 

[This link ]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352")might help to point you in the right direction and if you have questions, just ask. ;)

thnx for that!
cripes...there's a lot of stuff to 'digest'.......i guess that's why they call Windows "idiot proof", eh ?
still: UBUNTU is the easiest and most user-friendly of the LINUX installations, ain't it?.....think i read that some-where or others....
OK....i'll keep @ it.....gunna get stuck in tomorrow (New Year's Eve)
hopefully....i'll be in UBUNTU-land early 2015, eh?

(oh.....before i forget....Happy New Year to y'all and thnx for yr help, eh?  ):P )

cheers!

---

### Post by Bucky Ball on 2014-12-30
> **jimbo10 said:**
> [COLOR=#0000ff]thnx for that!
cripes...there's a lot of stuff to 'digest'.......i guess that's why they call Windows "idiot proof", eh ?
still: UBUNTU is the easiest and most user-friendly of the LINUX installations, ain't it?.....think i read that some-where or others....
OK....i'll keep @ it.....gunna get stuck in tomorrow (New Year's Eve)
hopefully....i'll be in UBUNTU-land early 2015, eh?[/COLOR]

(oh.....before i forget....Happy New Year to y'all and thnx for yr help, eh?  ):P )

cheers!

All sounds good. Yea, it's a learning curve, but once you have your system setup and know what you like and want, it's generally rock solid. At first, it can take a bit of getting stuck into to rearrange the approach to computing and Win brainwash. If you do that New Year's Eve cram or another one, you'll be getting closer by early 2015!

I run LTS releases and have a few partitions spare for 'playthings' (interim releases and other OSs), but you really don't even need to do that if you have reasonably powerful machine. You can try Linux OSs directly from the ISO using Virtualbox (in Software Centre) or other virtualisation software without installing. But I like to have a few options (like my main squeeze 14.04 LTS install and a couple of 12.04 LTS installs in case something falls over).

Anyhow, what I'm talking about is probably for later, but you see the possibilities. Once you have a fairly good idea of it, you can setup an install that won't fall over. My laptop sits on my desk and only gets switched off once or twice a year and it's been like that for ... when did I join the forums? ;)

PS: I install [the minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD")and only the programs I need/want. Took me a few years to work out what those programs were, but now it's there. Linux provides a flexibility and personalisation that Windows never coiuld for me.

---

### Post by Dreamer Fithp Apprentice on 2014-12-30
> **grahammechanical said:**
> May I suggest a method? . . . ++ on that. Hard to get confused that way. May I offer a slight edit, making explicit a few things assumed or implied and an alternative at one point? [I tried to set off Grahammechanical's lines with indentation but the forum won't let me indent - anyway, I think you can see what's mine, and what's plagiarized easily enough]

0.0-Remove any media in removable media drives or ports (cd, dvd, floppy, usb stick, etc.)
0.1-Shutdown the machine normally. When it is completely shutdown, unplug it.
     1) Disconnect the 250GB IDE drive.
1.1- Plug it back in and turn it on.

ALTERNATIVES, DEPENDING ON WHAT HAPPENS:
1.2_A-If you get a message from the bios complaining it has nothing to boot from, you have confirmed your belief about which drive windows was on. Insert the Ubuntu installation media (cd or usb stick) and reboot.
1.2_B- If Windows boots, you got it backwards. Shutdown normally; when it is completely off, unplug it; recconect the drive you disconnected and disconnect the one that was connected; start over at 1.1

ALTERNATIVE STEP 2s, DEPENDING ON WHAT YOU WANT:
Grahammechanical's suggestion is a wee bit easier:
    2) Run the Ubuntu installer with only the drive that doesn't have Windows connected and     choose the Erase Disk and Install Ubuntu option.

But I'd prefer:
2_B-the "something else" and partitioning for the reasons mentioned in my earlier post, qv. Either way will work.

    3) Test the loading of Ubuntu.
    4) Make sure that the BIOS has boot priority set to the SATA drive and not the IDE drive.
4.1-Shut down normally, either from a menu or shutdown button or "sudo shutdown -h now" in a terminal. Never connect or disconnect hard drives unless the machine is completely shut down, and preferably unplugged.
    5) Re-connect the 250GB IDE drive.
5.1-Plug it back in and boot.
    6) Load into Ubuntu and open a terminal and run

    ```
sudo update-grub
```

    See if the updating of Grub detects Windows. Reboot and see if you get a boot menu with     both Ubuntu and Windows as boot options. Test both operating systems.

---

### Post by jimbo10 on 2015-01-01
[COLOR=#0000cd]OK.....
just tried installing UBUNTU.... on me secondary HDD 
(after un-plugging the primary HDD/"c" drv)
here's what happened.....
installation via CD/DVD went OK.....
(i also dwn/ld all the doo-dads via WiFi modem.....which was connected during the install)
(i didn't use the "something else" option on the CD/DVD because i had trouble with it....i just used the "erase disc and install UBUNTU" option instead)

i re-booted, as per instructions......

then...nothing.....

nothing appeared "on screen".....
not even a 'cursor' AFA i could tell  :(

i thought it could be because UBUNTU wasn't recognising some hard-ware......
but......the install went OK....it seemed to recognise the mouse, key-board and LCD monitor....
and....even dwn/ld stuff using me WiFi modem....

OK....now what?

i'm stumped......:confused:

any hints/tips much appreciated!

ta!

(thank Christ i un-plugged me "c" drv first....OTW...i'd prblby be ***stuffed*** )

just checked the last post.....
[/COLOR][I][COLOR=#000000]Make sure that the BIOS has boot priority set to the SATA drive and not the IDE drive

[/COLOR][/I][COLOR=#000000]
could that be it?

there's no real facility in the BIOS to 'select' which HDD....apart from some-thing called Primary Channel 0 .....i might go and try that.....
[/COLOR][I][COLOR=#000000]
[/COLOR][/I][COLOR=#000000]hope that i don't hafta keep plugging and un-plugging HDDs though, eh?[/COLOR][I][COLOR=#000000]

[/COLOR][/I][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR]

---

### Post by jimbo10 on 2015-01-01
yipee!!   =d>

i got it going...i (simply) hadn't "saved" the BIOS setting......HDD boot priority......Channel2/master....

well....here i am in UBUNTU land.....  :mrgreen:
now.....i just gotta get the 'boot menu' set up..... vis a vis dual booting/Windows.....have unplugged the IDE drive ("c") drive.....

cheers y'all !
(hope y'all had a grouse New Year's Eve, eh?)

---

### Post by Bucky Ball on 2015-01-01
Good news. Plug the Windows drive in, boot to Ubuntu, open a terminal and:

```
sudo update-grub
```

With any luck, that's all you'll need. If they were on the same drive it should be, but on separate drives it may or may not be successful. If not, then Boot Repair is your friend. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Don't try and set-up grub without the Windows drive plugged in. If you end up using Boot Repair, just choose the 'Recommended Repair' option and see how you go. Take note of the bootinfoscript output Boot Repair creates and post the link here is Boot Repair fails to fix. Good luck. ;)

---

