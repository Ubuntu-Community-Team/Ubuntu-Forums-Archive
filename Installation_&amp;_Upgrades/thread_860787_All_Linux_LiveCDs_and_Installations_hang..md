---
title: "All Linux LiveCDs and Installations hang."
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by BuckleyInDaHouse on 2008-07-15
Well I tried a lot of Linux version from the DVD version to the live CD versions. All of them seem to hang at the installation. It only happens when I put in my new 1gb stick of ram. The ram is brand new and was checked for errors and it was clean.

I have a stock 512mb stick of ram that is pc3200 and the new 1gb stick is pc3200 also. Windows xp and vista both boot fine and run fine with both sticks in but when I try to run a LiveCD or install Linux it hangs. The Ubuntu LiveCD hangs after it moves up around 4-5 lines in the loading bar. I tried taking off the quiet splash noacpi pci=off everything. I don't know what the problem if anyone has some idea's please don't hesitate to post. if I missed any necessary details please let me know and I will post them.

Thanks, 
  Buckley.

---

### Post by BuckleyInDaHouse on 2008-07-16
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00303941&lc=en&cc=us&dlc=en&product=459879&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00303941&lc=en&cc=us&dlc=en&product=459879&lang=en)

Those are my computer specifications.

---

### Post by VMC on 2008-07-16
So the livecd boots ok using the 512mb ram. Then you insert another 1gb ram for a total of 1 1/2 gb ram and then it locks up. Is that correct? But Windows it works ok. Also check from Windows if it sees all the ram.

Also swap the ram around. Put the 1gb in first then the 512mb. I'm not sure exactly how this is configured.

---

### Post by wpshooter on 2008-07-16
1) I assume you have checked the Ubuntu CD's integrity by running the verification function that is found on the initial Ubuntu boot screen menu.

2) Have you tried to install from the ALTERNATE (text based) CD version ?

3) Have you considered resetting ALL of your BIOS settings back to the defaults.  IF, you do this make sure that you write down or know what the ALL of the parameters were set at before you reset to defaults.

4) And in particular, is there any chance that you have the ECC parameter enabled in the BIOS. If so, try disabling that.

---

### Post by BuckleyInDaHouse on 2008-07-16
> **VMC said:**
> So the livecd boots ok using the 512mb ram. Then you insert another 1gb ram for a total of 1 1/2 gb ram and then it locks up. Is that correct? But Windows it works ok. Also check from Windows if it sees all the ram.

Also swap the ram around. Put the 1gb in first then the 512mb. I'm not sure exactly how this is configured.

Thats correct, Windows sees all the ram and i checked the ram. I also swapped them around and same results.

> **wpshooter said:**
> 1) I assume you have checked the Ubuntu CD's integrity by running the verification function that is found on the initial Ubuntu boot screen menu.

2) Have you tried to install from the ALTERNATE (text based) CD version ?

3) Have you considered resetting ALL of your BIOS settings back to the defaults.  IF, you do this make sure that you write down or know what the ALL of the parameters were set at before you reset to defaults.

4) And in particular, is there any chance that you have the ECC parameter enabled in the BIOS. If so, try disabling that.

1. Yes i have and tried multiple CD brands.

2. No i haven't tried, I will now though.

3. No i haven't, I havent editted my bios. They aren't even edittable besides if i want my pci to be my main graphics card or my integerated.

4. Can't edit anything like that in the bios.

---

### Post by wpshooter on 2008-07-16
> **BuckleyInDaHouse said:**
> Thats correct, Windows sees all the ram and i checked the ram. I also swapped them around and same results.



1. Yes i have and tried multiple CD brands.

2. No i haven't tried, I will now though.

3. No i haven't, I havent editted my bios. They aren't even edittable besides if i want my pci to be my main graphics card or my integerated.

4. Can't edit anything like that in the bios.

Not editable !!! How old is this machine ?  Are you sure you are looking it the correct place ?  Most any even fairly modern machine will have **dozens** of various BIOS parameters, which can usually be set back to the default or fail safe parameters by a choice on the exit menu.

---

### Post by BuckleyInDaHouse on 2008-07-16
I managed to get the alternate cd too load and install but it comes up with alot of bash errors something about commands not found   and I just then I typed "/usr/bin/sudo gdm" and it loads it up but I can't login.

---

### Post by wpshooter on 2008-07-16
Are you burning the ISO image at 4x or less ?

Are you checking the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu, note this is different place from doing a sumcheck on the ISO image ?

---

### Post by BuckleyInDaHouse on 2008-07-16
Yea i done all the simple common sense stuff.

---

### Post by VMC on 2008-07-16
There's something up with using that extra ram. If all works okay using 512mb, and doesn't using another ram slot, then it points to hardware. Windows works okay, but ubuntu doesn't. That's kind of weird. Have you tried another distro for reference.

Is there a difference on the ram. One being single-side and the other double-sided?

Try this using a Terminal, and check the ram slots:

```
sudo lshw
```

---

### Post by BuckleyInDaHouse on 2008-07-17
> **VMC said:**
> There's something up with using that extra ram. If all works okay using 512mb, and doesn't using another ram slot, then it points to hardware. Windows works okay, but ubuntu doesn't. That's kind of weird. Have you tried another distro for reference.

Is there a difference on the ram. One being single-side and the other double-sided?

Try this using a Terminal, and check the ram slots:

```
sudo lshw
```
Well I cannot do the terminal suggestion you posted because when I tried the Alternate CD i formatted my hard drive once again(8th) and it didn't work. This happens to be the case with all Linux Distros (OpenSUSE, Fedora, Ubuntu, Mandrivia(sp?)) and I really do not feel like formatting and installing the bloatware we call windows again. Wasted like 4 days in a row total if you add up all the windows installations I've done lol.

I did check the ram and one is double sided meaning it has black squares Im guessing memory chips on both sides the 1 gb does. And the 512 is single sided. Think this may affect something? if so let me know, I still got 13 days until my warranty is up for a return back to Fry's.

Heres the ram i got.
[http://computers.pricegrabber.com/laptop-memory/m/2462892/details/st=product_tab/](http://computers.pricegrabber.com/laptop-memory/m/2462892/details/st=product_tab/)

Another link has more info i think: [http://www.buy.com/prod/corsair-value-select-1gb-pc3200-400mhz-184-pin-ddr-memory/q/loc/101/10364700.html](http://www.buy.com/prod/corsair-value-select-1gb-pc3200-400mhz-184-pin-ddr-memory/q/loc/101/10364700.html)

---

### Post by Sef on 2008-07-17
> I did check the ram and one is double sided meaning it has black squares Im guessing memory chips on both sides the 1 gb does. And the 512 is single sided. Think this may affect something? if so let me know, I still got 13 days until my warranty is up for a return back to Fry's.

Have you run the mem86 test? (Run it for about 8 hours.)  It is not clear from your post if you have or not.

---

### Post by BuckleyInDaHouse on 2008-07-17
I didn't test my ram with memtest because when it starts my fans stop spinning and my cpu gets overheated and causes the PC to shutdown. I ran the test with programs that run while windows is up.

---

### Post by eldragon on 2008-07-17
once under windows (after a failed linux boot).

install the ext3 windows drivers from here [http://www.fs-driver.org/](http://www.fs-driver.org/)

then go to /var/log/kern.log or /var/log/kern.0.log
and post the last 20 lines from that file here........

it should shed some light on when is hanging, or which kernel module is going crazy.

---

### Post by BuckleyInDaHouse on 2008-07-17
> **eldragon said:**
> once under windows (after a failed linux boot).

install the ext3 windows drivers from here [http://www.fs-driver.org/](http://www.fs-driver.org/)

then go to /var/log/kern.log or /var/log/kern.0.log
and post the last 20 lines from that file here........

it should shed some light on when is hanging, or which kernel module is going crazy.
Will do, I saw something about a log on the filesystem but im like wtf? I cant boot to read it and windows cant read it..dumb ubuntu lol.

---

### Post by BuckleyInDaHouse on 2008-07-17
> **eldragon said:**
> once under windows (after a failed linux boot).

install the ext3 windows drivers from here [http://www.fs-driver.org/](http://www.fs-driver.org/)

then go to /var/log/kern.log or /var/log/kern.0.log
and post the last 20 lines from that file here........

it should shed some light on when is hanging, or which kernel module is going crazy.
-Bump-

[img]http://i37.tinypic.com/ivekjb.jpg[/img]

I get this error when I try to mount the Ext3 Filesystem (K:).
What should I do?

---

### Post by eldragon on 2008-07-21
> **BuckleyInDaHouse said:**
> -Bump-

[img]http://i37.tinypic.com/ivekjb.jpg[/img]

I get this error when I try to mount the Ext3 Filesystem (K:).
What should I do?

all i can say is ouch........

you could always boot an alternate install cd, but do not install, once the kernel loads, you can hit ctrl-alt-f2 to go to another terminal an there do
```

# mkdir /target2
# mount /dev/sda1 /target2
# umount /target2

```
just remember the # means you ought to do this as root. (or super user). i dont remember what state the alternate cd leaves you, but if the prompt ends with a pound sign(#) you are good to go, if its a dollar sign($), then append sudo to those commands.

that should mount /dev/sda1 on /target2 and then unmount it. replace sda1 with the name of your device. to get a list of devices do:
```

ls -alh /dev | grep sd

```

after unmounting, the fs-driver should work ok.


good luck

---

