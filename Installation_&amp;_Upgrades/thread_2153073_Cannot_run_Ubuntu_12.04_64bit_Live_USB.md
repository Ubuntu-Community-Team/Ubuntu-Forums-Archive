---
title: "Cannot run Ubuntu 12.04 64bit Live USB"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by SangeetKhatri on 2013-06-10
Yesterday I downloaded the official Ubuntu 12.04.2 LTS Version because i wanted to reinstall Ubuntu because of some new partitions and i made a bootable USB using "Unetbootin" "Startup Disc Creator" and from many other bootable USB creator softwares and none off them worked and some of them showed this error [http://paste.ubuntu.com/5749088/](http://paste.ubuntu.com/5749088/)

Then i thought that there must be some problem in my iso so i redownloaded it and still it is giving me the same error.

When i start the USB it asks for options like "Run Ubuntu without Installation" "Install Ubuntu" and some more options. But none of them can let me boot the USB.

And when i use the Live USB made by Unetbootin then the error shows something like  "Corrupt or Invalid Kernel Image". 

How is all that possible. I downladed both times from the official site and i used torrent which is very less likely to change the file and also i checked the MDA5 sum and it is exactly the same. Then what is the problem?

Please guys help me i cannnot reinstall Ubuntu and i have to do some homework on "Javascript" . Please guys help me.

Any help is highly appreciated.
Thanks

---

### Post by ohnonot on 2013-06-10
i recently installed three ubuntu flavors.
i had problems with unetbootin; i solved it by making the usb's thus: stick the usb in. does it show up in your file manager? then open a terminal and type 'mount' without any arguments. here, it says:> ...
/dev/sdc1 on /media/me/12fe51dd-0a7b-43f4-878d-35241aff5db6 type ext4 (rw,nosuid,nodev,uhelper=udisks2)so /dev/sdc1 is my usb stick. make 100% sure! then type:```
sudo dd if=/path/to/your/ubuntu.iso of=/dev/sdX
```where sdX is your usb.  'of=/dev/sdc' would be the right value, not sdc1.

_**big fat warning:**_
dd (nickname disk destroyer) is a very powerful and potentially dangerous tool! if of= (output file) is set to a wrong value, data loss may occur!
maybe the sudo is not needed when copying to usb-stick.
also you may need to unmount the stick before executing dd (umount /dev/sdc1).

---

### Post by SangeetKhatri on 2013-06-10
Did everything you said and the Live USB was made in about 5 minutes but still it is not working and showing the same error:

[http://paste.ubuntu.com/5749088/](http://paste.ubuntu.com/5749088/)

It shows the Ubuntu Boot Screen for about half an hour and then gives this Error Message. I am pissed off as i cannot install Ubuntu.

Is the fact that i am running the same version of Ubuntu which i am trying to reinstall making the USB not boot properly?

Please help me
Thanks

---

### Post by ohnonot on 2013-06-10
right. you could of course try to format the usb stick first and then try the dd thing again, but i'm 90% sure that you're problem is a different one.
it shouldn't have anything to do with the installed version, but what exactly is this boot screen that you see? could you take a pic of it?

also, the code you pastebinned, i can't interpret that so i humbly call this to the attention of someone more knowledgable.

---

### Post by SangeetKhatri on 2013-06-10
The installation screen is the default Ubuntu one with pinkish background and white Ubuntu logo with 4 dots below the logo. Exactly like the one in the pic at [http://www.thefanclub.co.za/sites/default/files/styles/300-wide/public/images/howto/ubuntu-boot-splash.png?itok=9AT2L2e9](http://www.thefanclub.co.za/sites/default/files/styles/300-wide/public/images/howto/ubuntu-boot-splash.png?itok=9AT2L2e9)

Another thing is that when i press any button from "F1" to F12" I get an error message which says every 2-3 seconds the below lines

```
[COLOR=#000000][FONT=arial][FONT=Arial]stdin:/ I/O Error[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=Arial]/init: line 7: can't open /dev/sr0: No medium found[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=Arial]/init: line 7: can't open /dev/sr0: No medium found[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=Arial]stdin:/ I/O Error[/FONT]
```
[FONT=Arial]

And the same message goes on to be displayed every time i press any button from "F1" to "F12"
[/FONT]
I am trying to run the "64 bit" Ubuntu on a laptop with 4GB Ram. I think it has nothing to do with RAM or is it?

Anyways thanks for replying.

[/FONT][/COLOR]

---

### Post by sudodus on 2013-06-10
I could not get much from the pastebin either, except that it cannot run blkid (that should list block ID of the partitions). So there is something very wrong.

In order to give advice, we need to know more.

- Is any installed system running (well, badly or not at all)? Ubuntu, some other system?

- Can you boot another computer with the live USB drive?

- Please specify your computer, at least cpu, ram and graphics chip/card, wifi chip/card

- Have you checked the RAM with memtest from the second menu when you boot from from the USB drive (after the language selection)?

My only guess right now is bad RAM.

---

### Post by SangeetKhatri on 2013-06-10
- Ubuntu 12.04 was installed but i just removed it and installed Lubuntu 13.04 because it got corrupted because of my some mistrake. So now i have Lubuntu 13.04 installed temporarily for the time i cannot install Ubuntu 12.04

- Nope, i cannot run Ubuntu 12.04 64 bit from my father's netbook too. It gives the same error and stuff (The netbook has 2GB ram which is not suitable for 64 bit though)

- My laptop is Acer Aspire 5738, core2duo , 4GB DDR2 RAM, No Graphics Card, No idea about wifi chip, but searching the laptop specs would get you more specs.

- I checked my RAM with memtest and it passed the test and it was said to be 100% fine by the memtest tool.

Hope that helps.
Thanks

If you want to have more information, feel free to ask me. Currently i am running Lubuntu 13.04 just temporarily.

---

### Post by sudodus on 2013-06-10
If you can run Lubuntu (from CD/USB/HDD, whatever works, please use the following commands to try to find out about the graphics chip

```
 sudo lshw>lshw.txt
```

and look at the file with a file editing

```
 leafpad lshw.txt
```

and

```
 hardinfo
```

---

### Post by SangeetKhatri on 2013-06-10
Here is the output of lshw at [http://paste.ubuntu.com/5752883/](http://paste.ubuntu.com/5752883/)

---

### Post by SangeetKhatri on 2013-06-10
And i have natively installed Lubuntu and am not running it from live CD or Live USB. Though i installed it using Live USB

---

### Post by sudodus on 2013-06-11
The output of lshw looks good to me. There is intel graphics, which should work with Ubuntu. There is one questionmark for the wifi chip, but usually Intel wifi works with Ubuntu.

You wrote that you have tried to boot from Unetbootin and Startup Disc Creator.

1. Did you try the dd method described by *[COLOR=#000000]ohnonot[/COLOR]*? And you are sure that the image was written to the USB drive?

```
 sudo dd if=/path/to/your/ubuntu.iso of=/dev/sdX
```

In that case, did you really get the same result as with Unetbootin?

2. Then I suspect that the downloaded image is bad. Please check again **the whole iso file with md5sum**, that it matches what is posted in [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

3. If the md5sum matches, I suggest that you try another sub-version alias point-release of Ubuntu 12.04. You tried the newest one 12.04.2, so **try either of 12.04, 12.04.1**, I would suggest 12.04.1, which is more debugged and polished than the original one.

4. I suggest that you download and use my script to make imaging with dd safer. See [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073"). This method has a high success rate, partly because it does not depend on previous formatting of the USB drive.

---

### Post by SangeetKhatri on 2013-06-11
There is nothing wrong with md5 sum. The MD5 sum of the file is exactly same as the MD5 given in the site.
Well.. let me just try 12.04.1 It would take about 4 hours download then i will tell you.

If there is any further problem after than then i would post it here, otherwise would mark this thread as [SOLVED]

Thanks

---

### Post by sudodus on 2013-06-11
Have you tried to get it via ***torrent***? It is usually faster.

---

### Post by SangeetKhatri on 2013-06-12
I downloaded two more Ubuntu 12.04 iso's first one was the 32 bit 12.04.2 and the second one was 64 bit 12.04.1 and both of them gave the same error. Why the hell can't i run it. Do you know anyone who knows what those error messages mean? Because i am sure something must be there in those error messages. 

And i always use torrents.

The difference this time was that Live USB made by Unetbootin did not showed any error which it showed with 64 bit 12.04.2 which was "corrupt or invalid kernel" But still it is not loading. Can you please help me? Or pass this to someone who actually knows what those error messages mean because i am really pissed off.

I have downloaded the Ubuntu 12.04 iso four times and none of them is working. While at the same time Lubuntu 13.04 Live CD is easily working.

I remember that when i first tried Ubuntu 12.04 around 4-5 months ago then it worked fine from Live USB on the same laptop, then what must be the thing that is causing problems??

---

### Post by ohnonot on 2013-06-12
> **SangeetKhatri said:**
> Another thing is that when i press any button from "F1" to F12" I get an error message which says every 2-3 seconds the below lines
```
[COLOR=#000000][FONT=arial][FONT=Arial]stdin:/ I/O Error[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=Arial]/init: line 7: can't open /dev/sr0: No medium found[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=Arial]/init: line 7: can't open /dev/sr0: No medium found[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=Arial]stdin:/ I/O Error[/FONT]
```
[FONT=Arial]

And the same message goes on to be displayed every time i press any button from "F1" to "F12"
[/FONT]
[/FONT][/COLOR]
sudodus certainly has good advice on this, but this error message brings 2 things to mind:

- iirc,  /dev/srX is used for cd drives, not usb? 
so the question would be, did you install Lubuntu from the exact same media? the same usb stick? or from a cd?
(afaiu you managed to install Lubuntu on the same machine?)
- what does line 7 of /init read? (you might have to search for the init script on your installation medium, it's not necessarily in the root dir)

...could the usb stick itself be corrupt? or badly formatted, as both sudodus and me touched already earlier.
that would mean, create a new partition table, then format it to fat32 (sometimes also called FAT win95 or some such nonsense) you can do it conveniently with gparted, but there's other tools.

i don't feel too confident with driver related stuff - but i would like to add to my first post (post #2 of this thread):
finding out which device name is your actual usb stick is very important.
i usually go this way before putting an .iso on a usb stick with dd:
fire up **gparted**, change the display to the usb stick (right-click the drop-down in the top right).
that gives me the name of the device. at the same time i wipe it really clean with creating a partition table and formatting to fat32.
then i close gparted and do the dd thing.
so, if you want to make 100% sure, try this again.

---

### Post by sudodus on 2013-06-13
+1 to *ohnonot*'s advice

and I suggest that you try the dd method (which is made safe with the following method: cut and paste to get the script, and use it to guide the choice of USB device; it helps you replace X with the correct drive letter)

[Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

Recently some people have had problems with Unetbootin. Normally it is a very reliable tool, but maybe there is a temporary problem, and you should try another method. And the dd method has a high success rate.

If still no go, we should look for the error somewhere else, for example some of the hardware.

---

### Post by SangeetKhatri on 2013-06-13
@ohnonot

I booted and installed Lubuntu from the same USB using unetbootin only and it worked flawlessly. 
And i am sorry i could not find any /init file in my USB drive. Why so? Anyways here is the screenshot [http://i.imgur.com/J7FoI8b.png](http://i.imgur.com/J7FoI8b.png)

And i correctly formatted the USB to fat32 using a Windows 7 netbook. And in gparted too it says the same. and since i was able to boot off Lubuntu and even install it, hence i think the USB is just fine.

OK, anyways i will try what you suggested and would report if i get any further problems. As for now stuck with Lubuntu though.

---

### Post by SangeetKhatri on 2013-06-13
@sudodus Man.. that page is confusing me a lot. I am not that much aware with those scripts and other stuff. Can you please simplify it for me to understand. Please..

---

### Post by sudodus on 2013-06-13
The simpest thing is to use ohnonot's method described in post #2,

```
 sudo dd if=/path/to/your/ubuntu.iso of=/dev/sdX
```

but double-check that you will be writing to the correct drive. If the internal drive is /dev/sda, and there is no other drive except the USB drive, that drive is /dev/sdb. If you have also other drives connected, it might be /dev/sdc, dev/sdd etc. So it is important that you identify the drive you want to use. If you write to another drive, that drive will be overwritten and its content will be lost.

***Still, that single line suggested by ******ohnonot is the simplest method available.*** One single command. It cannot be simpler. You need no pre-formatting. The only thing is that you have to write to the correct drive. If you are confused by my script, that is intended to help you avoid writing to the wrong drive, don't use it. Check manually, make sure there is no typing error and run that dd command line.

Ask and ask again, until you are confident that  you know which device letter is used for the USB drive, that you want to  make into a live USB drive. For example, do you know which commands that will help you identify it?

Good luck :-)

---

### Post by SangeetKhatri on 2013-06-13
I am finally happy to announce that.... that....that.........................!!!

Yes, guys you guessed it right. The problem has been solved and i have now installed the beautifull Ubuntu 12.04 with Unity which is so awesome. Thank You guys a lot.

The actual problem was that the pen drive which i used earlier had some problem with Ubuntu 12.04, i do not know why. I just got a pen drive of a friend and made the Live USB to his USB using the DD method. And it worked flawlessly like it used to work before.

So, sorry for all the inconvenience it was the Pen Drive that was causing problems.

So my advice for anyone who get's caught in problem like this would be to just get a spare Pen Drive from a friend and just try to boot it off from that USB and as in my case chances are that it would work just fine..!!

Anyways guys thankyou, you showed a lot of patience in dealing with somewhat impatient guy like me. And i am finally so happy that i have finally got a real OS installed in my laptop. LXDE, XFCE, Cinnamon they all are not even close to Ubuntu's Unity. And i am just loving the Unity Experience so far. Nothing to set up that much and changing settings very easy. Easiest i found on Linux so far and i have also used Linux Mint 14 by the way,

Anyways guys again a big thanks and sorry for the fact that the problem was in the USB.

Bye

---

### Post by sudodus on 2013-06-14
Congratulations :KS

Before returning the USB drive to your friend, you might need to wipe it as desribed in this link

[Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

and make a new partition table and a new FAT32 file system with gparted.

---

