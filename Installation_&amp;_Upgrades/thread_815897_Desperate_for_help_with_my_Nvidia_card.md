---
title: "Desperate for help with my Nvidia card"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Radoka on 2008-06-02
Got a problem with the Hardy Heron release that's freaking me out. I've searched both this forum and the internet since the release date but I can't find a cure anywhere...

As the subject says it's all about my Nvidia 7300 card. The software accelerated drivers work fine but when I install the real drivers the problem occurs. It doesen't matter how I install the drivers, it ends up with a black screen and the computer doesn't respond to any keyboard activity as ctrl-alt-f1 or something like that. The monitor doesn't turn off, it just doesn't show anything. Holding the power buttonis the only way to kill it.

The installation methods I've tried over and over again for more than a month is:
1. Ubuntus restricted drivers manager
2. Envy NG
3. Downloading the drivers from Nvidias website and install it manually

I've also tried these three methods from clean installations. I've reinstalled Ubuntu at least 5 times to fix this.

Can someone please help me find a solution? I dont want to go back to Gutsy. (It worked fine in Gutsy and all other releases since 5.10) And i want to play World of Warcraft again! :(

Some relevant information: I've got a Amd64 installation with a rt-kernel (Ubuntu Studio)

Edit: My /var/log/Xorg.0.log doesn't contain any erors. Everything seemes fine.

---

### Post by kellemes on 2008-06-02
Don't have a NVidia myself..
It may help to find the exact version of the driver you used on Gutsy and try to install this version of the driver on your current install?

Are you sure /var/log/Xorg.0.log doesn't hold any informative data,  obviously after a failed session..
Maybe you can post it (between CODE-tags), I'd be interested.

---

### Post by Peter09 on 2008-06-02
This may not help you but:-

I have experienced exactly the same problem. The card worked fine when not being expected to do any onboard acceleration type effort. As soon as I installed 'proper' drivers I had exactly the same fault as you have.

It was a new card and it turned out to be a hardware fault. It might be worth checking that the card is seated properly and it is connected ok.

As I have said earlier I am not sure this is going to help but just in case.

PC

---

### Post by Radoka on 2008-06-03
Finally I found a way to post the Xorg.0.log file here. First it was wrong file type, then it was too big... :)

Well, as I said: I couldn't find any wrong with it but maybe I missed something. I will also try Peter09's suggestion but it seemes not likely since it stopped working the same minute I switched OS. But stranger things have happened in this world. :)

Thanx for your reply!

---

### Post by Pyrdracon on 2008-06-03
Hello,

I experience exact the same problem here. I installed Ubuntu Hardy Heron some days ago, just to see the differences between this distribution and openSUSE, which runs without big problems on my computer.

But when I tried to install the nVidia drivers under Ubuntu my computer did not respond to any action I made. The NumLock LED did not respond and there was no posibility to log in with ssh from another computer. With openSUSE the driver installation with the original drivers (same drivers with Ubuntu) from nVidia worked without problems.

In the syslog and Xorg.0.log are no hints that something went wrong and it doesn't matter if I use either of the three mentioned methods to install the driver.

Currently I have installed the 2.6.24-17-generic kernel and tried to install the actual NVIDIA-Linux-x86-173.14.05-pkg1.run driver. At the moment I only can use the NV driver but I'd really like to run some 3d programs.

CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
GPU: nVidia GeForce 8600 GT

Michael

---

### Post by Radoka on 2008-06-03
In some way I'm glad someone else has experienced this thing... It's even better if someone know what's the problem! ;) Is it maybe a bug in some way?

---

### Post by Radoka on 2008-06-04
Yesterday I saw that updates för nividia-glx-new and the kernel restricted modules package so I installed them and tried once more for the 999999999 time but same thing: Black screen, computer doesn't respond to anything.

I'm not new to Linux after at least 10 years with it but I can't sort this out! I don't want to switch OS, because I like Ubuntu so much but I haven't been able to use my computer fully in nearly two months now so I don't know what to do... :(

---

### Post by PmDematagoda on 2008-06-04
Can you post the output of:-
```
lspci | grep VGA
```

---

### Post by nantax on 2008-06-04
Not sure if this would help, but this was the steps I followed to install the new nvidia graphics driver without envy.
[URL="http://http://ubuntuforums.org/showthread.php?t=813581"]
http://ubuntuforums.org/showthread.php?t=813581[/URL]

---

### Post by Smudgers on 2008-06-04
Hi everyone,

Brand new to Ubuntu (in fact to Linux). So far I like what I'm finding, BUT I too am having great problems with Nvidia drivers and Hardy Heron. 

I to am getting a totally blank screen which can only be removed by a reboot and reinstall.

Have tried drivers from Nvidia and the driver that comes with the 8.04 install disk - both have exact same effect.

I have FX 5200 card with Pentium 4 3Ghz

Any help would be great

Smudgers

Just remembered, I tried using different monitors, and one monitor would indicate that it was entering "power save" mode which it would normally do after the PC has gone into power down mode. Is the graphics card being turned off ?????

Output from lspci is
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by Radoka on 2008-06-04
My output from lspci | grep VGA is:
05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

nantax: Thanx for the link! Remember trying that...

---

### Post by Peter09 on 2008-06-05
I have just installed Hardy on a friends machine, which was running Gutsy. I am now getting a similar problem. I can reach the login prompt, but when I login I get a black screen with a white box in the corner. I can recover to the login prompt with control-Alt-Backspace.

The interesting thing is that if I disconnect the network, just before logging in (not during boot) then I can login successfully. Putting the lead back into the machine once logged in gives a functioning network as well.

Although some of the symptoms are different with you it might be worth a test.:)

PC

---

### Post by Radoka on 2008-06-05
Today I'll format my hard drive and install Gutsy Gibbons instead to be able to use this machine as I want. I'm really disappointed of the fact that Hardy Heron doesn't work on a computer with such common hardware that I have. I can only hope that next release is better. :(

Edit: Sorry for the bitterness in this post: I'm just tired and sad. I had bad luck - that's all. :)

---

### Post by zedstrange on 2008-06-11
> **Radoka said:**
> My output from lspci | grep VGA is:
05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)


lucky you,   all i got was 
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

:(

---

### Post by Radoka on 2008-07-16
Finally solved it in some way... Got myself a new graphics card and now everything is working. Still don't know what was wrong. I don't think the card was broken.

---

