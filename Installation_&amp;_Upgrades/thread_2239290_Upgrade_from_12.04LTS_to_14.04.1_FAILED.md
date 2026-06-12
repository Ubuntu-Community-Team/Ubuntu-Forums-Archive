---
title: "Upgrade from 12.04LTS to 14.04.1 FAILED"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by Andrew_Sinclair on 2014-08-13
I have just attempted to upgrade using the Update Manager. Everything seemed to be going well until the system froze during the Install phase. If I reboot I get to the grub menu where selecting a Linux option just gets me to a blank screen. Luckily I have a dual boot system and selecting the windows option (reluctantly) at least allows me to write this message. Is there any way I can resume the upgrade process or am I now without a Linux system after having no problems using it since Hardy Heron.

---

### Post by kansasnoob on 2014-08-13
Trying to recover from a failed upgrade can be problematic and a fresh install may end up being needed. Did you at least have all your data backed up?

Should you need to reinstall, and since you're dual booting with Windows you need to be aware of this nasty bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You could try a few commands if you boot to Ubuntu and hit the black screen try entering a TTY using Ctrl+Alt+F1, then login as usual and try:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

```
sudo apt-get dist-upgrade
```

```
sudo dpkg --configure -a
```

You may need to repeat any of those commands in no particular order and the output may provide details regarding the current state of the system.

---

### Post by interglossa on 2014-08-13
They took the extra step of putting this option right on the Update Manager with an 'Upgrade' button, which more or less sends the message that this is the default procedure for dealing with upgrades, which is clearly not the case in previous releases.  They need to either 1) remove the button or 2) test it enough to make it bullet-proof.

---

### Post by kc1di on 2014-08-13
> **interglossa said:**
> They took the extra step of putting this option right on the Update Manager with an 'Upgrade' button, which more or less sends the message that this is the default procedure for dealing with upgrades, which is clearly not the case in previous releases.  They need to either 1) remove the button or 2) test it enough to make it bullet-proof.

+1

I still advise most people to do a fresh install seem much less problematic.  Just back up everything important to you,  to cloud or external drive/usb stick first.

---

### Post by kansasnoob on 2014-08-13
> **interglossa said:**
> They took the extra step of putting this option right on the Update Manager with an 'Upgrade' button, which more or less sends the message that this is the default procedure for dealing with upgrades, which is clearly not the case in previous releases.  They need to either 1) remove the button or 2) test it enough to make it bullet-proof.

Upgrades have been offered via update manager as long as I can remember and I've been using Ubuntu since Gutsy. We can always use more testers, I was the only independent tester to test the 14.04.1 upgrades:

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73744/testcases/1635/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73744/testcases/1635/results)

They are also tested internally by Canonical but a lot of things can effect the outcome of a release upgrade, particularly the use of PPA's or the use of any non-standard packages that may have been installed from any source other than the Ubuntu repos.

---

### Post by oakridge on 2014-08-13
My questions seems closely related to this post so I hope you will excuse me for butting in.

Update manager has recently advised me that I can update from 12.04LTS to 14.04LTS so I clicked the Upgrade button but I quickly had a error message saying that my graphics card is not compatible with the upgrade and I should continue to use the LTS version for the time being which is what I thought was happening.

I am upgrading a Ubunto only machine but I also have a dual-boot machine paired with Windows 7.  I was advised a while ago that that the upgrade is not reliable with dual boot machines.  Do you know whether this problem has been resolved?

Malcolm

---

### Post by kansasnoob on 2014-08-13
> **oakridge said:**
> My questions seems closely related to this post so I hope you will excuse me for butting in.

Update manager has recently advised me that I can update from 12.04LTS to 14.04LTS so I clicked the Upgrade button but I quickly had a error message saying that my graphics card is not compatible with the upgrade and I should continue to use the LTS version for the time being which is what I thought was happening.

I am upgrading a Ubunto only machine but I also have a dual-boot machine paired with Windows 7.  I was advised a while ago that that the upgrade is not reliable with dual boot machines.  Do you know whether this problem has been resolved?

Malcolm

Two different issues:

> Update manager has recently advised me that I can update from 12.04LTS to 14.04LTS so I clicked the Upgrade button but I quickly had a error message saying that my graphics card is not compatible with the upgrade and I should continue to use the LTS version for the time being which is what I thought was happening.

Well 12.04 (Precise) offered Unity-2D and 14.04 does not so maybe you're stuck with Precise. Please post the output of this command:

```
uname -r
```

We need to see that output to know if you're effected by [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL").

> I also have a dual-boot machine paired with Windows 7.  I was advised a while ago that that the upgrade is not reliable with dual boot machines.

I'm not aware of any dual-boot specific problems regarding release upgrades, but release upgrades can be problematic and many long time Ubuntu users recommend fresh installs. I think all users should hope for the best but assume the worst could happen which means creating a full backup of anything important before performing a release upgrade or any reinstallation!

Dual-booters should be acutely aware of this OS/data eating killer bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

But if you're running Precise with the original kernel and X-stack why not just relax since it's supported until April 2017? Of course Precise users that installed with the 12.04.2, 12.04.3, or 12.04.4 media face the aforementioned HWE EOL - more about LTS support and HWE here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

BTW, in the future start a new thread regarding each individual issue/question :)

---

### Post by kc1di on 2014-08-13
you should start a separate thread for this as it is slightly different. 
How ever as far as I know which isn't much - the upgrade works ok if it works you'll have to re due grub, I still think the best way is to do a fresh install.
The problem with your video card must be that it's older.  If it's Nvidia I know they dropped a bunch of them when xorg was upgraded to newer version. Because they were not compatible with the new xorg structure.  So you may be out of luck with that card. 
I always advise that you back up any important data wether or not your doing the upgrade or fresh install.  
Have fun ;)

---

### Post by kc1di on 2014-08-13
hi kansasnoob, You beat me to it by about 10 seconds :) 
your post is much more in depth - thanks :)

---

### Post by oakridge on 2014-08-13
Thank you for your replies.

The response to uname -r
is
3.2.0-67-generic-pae

The graphics are on the motherboard which is:

AMD Athlon(tm) II X4 640 Processor × 4 

The OS is 32 bit - oops.

The graphics driver is 'unkown' and the experience 'standard'.

I had not realised the Precise is supported until 2017 and the prospect of doing a re-install especially with all the messing about with Microsoft installation keys is more than a little daunting.  Perhaps I will stay as I am, especially as I will be 74 by then.

Malcolm

---

### Post by kansasnoob on 2014-08-13
> **oakridge said:**
> Thank you for your replies.

The response to uname -r
is
3.2.0-67-generic-pae

The graphics are on the motherboard which is:

AMD Athlon(tm) II X4 640 Processor × 4 

The OS is 32 bit - oops.

The graphics driver is 'unkown' and the experience 'standard'.

I had not realised the Precise is supported until 2017 and the prospect of doing a re-install especially with all the messing about with Microsoft installation keys is more than a little daunting.  Perhaps I will stay as I am, especially as I will be 74 by then.

Malcolm

OK ........

> The response to uname -r is 3.2.0-67-generic-pae

So relax, if you're running Ubuntu you're supported until April 2017 (other flavors varied in support duration), just keep applying normal updates and say no to the upgrade. You'll be reminded when Precise is approaching EOL :D

> The graphics driver is 'unkown'

Should probably see the output of:

```
lspci | grep VGA
```

You may (or may not) be able to improve the performance by installing a different graphics driver, but if it ain't broke don't fix it! OTOH it would be nice just to know what graphics chip you have. The info you posted is CPU (or APU) - I've yet to mess with any of the new APU stuff.

---

### Post by Andrew_Sinclair on 2014-08-13
Sorry about the lateness of the reply. First of all Thanks a heap  for being the first to respond to my plight although thanks to the others who have subsequently responded. The four options you suggested I tried in the following order     1) sudo dpkg...  
                                  2) sudo ... update
                                  3) sudo ... install
                                  4) sudo ... dist_upgrade

At the end of step 4) I had what appeared to be 14.04.1 installed with my internet connection , email, desktop etc present. Is there some way I can verify that I have a legitimate LTS 14.04?

uname -r yielded     3.13.0-33-generic.

I am testing a few things out . Booting had messages being displayed. Not sure whether these are deficiencies or problems or both. Have noticed that the DevHelp window does not display correctly. The left option box has been truncated. 

Thanks also about the tip regarding the Windows bug, but to be quite frank, the less I rely on Windows the better off I will be and feel.

Any way, Thanks again. It appears as if I have my system back!!

ps sorry about the lack of technical jargon.

---

### Post by kc1di on 2014-08-13
You can go to System settings > Details 

the first page that  shows it gives you the version of ubuntu installed.

---

### Post by Andrew_Sinclair on 2014-08-13
Firstly thanks a heap for being the first to respond, although thanks to the others who subsequently responded. You suggested trying four things and I did in the following order:
1) sudo dpkg...
2) sudo...update
3) sudo ... install
4) sudo ... dist-upgrade.

The result is I think I have my system back although I am trying a few things out. I have my internet connection, email service, desktop etc.
 I tried uname -r and this yielded 3.13.0-33-generic.
Booting is not totally clean as there are messages displayed and I don't know whether they are deficiencies or problems or both.
Is there any way that I can verify that I have a legitiamet 14.04LTS upgrade?

Thanks also for the tip about the Windows bug. However to be quite frank, the less I rely on Windows the better off I will feel and be.

Thanks again.

---

### Post by kansasnoob on 2014-08-13
> **Andrew_Sinclair said:**
> Sorry about the lateness of the reply. First of all Thanks a heap  for being the first to respond to my plight although thanks to the others who have subsequently responded. The four options you suggested I tried in the following order     1) sudo dpkg...  
                                  2) sudo ... update
                                  3) sudo ... install
                                  4) sudo ... dist_upgrade

At the end of step 4) I had what appeared to be 14.04.1 installed with my internet connection , email, desktop etc present. Is there some way I can verify that I have a legitimate LTS 14.04?

uname -r yielded     3.13.0-33-generic.

I am testing a few things out . Booting had messages being displayed. Not sure whether these are deficiencies or problems or both. Have noticed that the DevHelp window does not display correctly. The left option box has been truncated. 

Thanks also about the tip regarding the Windows bug, but to be quite frank, the less I rely on Windows the better off I will be and feel.

Any way, Thanks again. It appears as if I have my system back!!

ps sorry about the lack of technical jargon.

More than one thing so one at a time:

> Is there some way I can verify that I have a legitimate LTS 14.04?

Check the output of:

```
lsb_release -a
```

Also run one more time:

```
sudo apt-get -f install
```

If that complains about missing dependencies or such you still have a problem.

> Booting had messages being displayed. Not sure whether these are deficiencies or problems or both.

That's quite common on the first boot. It's almost like some things need one reboot to configure. You can look in /var/crash and probably find several corresponding crash reports that were sent to [Ubuntu errors]("https://errors.ubuntu.com/"). let us know if subsequent reboots don't improve.

> Have noticed that the DevHelp window does not display correctly. The left option box has been truncated. 

I've never used it - could it be app specific?

One thing that comes to mind is that you may (or may not) want to explore Additional Drivers for your specific graphics chip. Would you please post the output of:

```
lspci | grep VGA
```

That can always be a bit of a scary proposition. Sometimes the available proprietary drivers help and sometimes they only hose things :(

---

### Post by gabmuks on 2014-08-14
> **kansasnoob said:**
> Trying to recover from a failed upgrade can be problematic and a fresh install may end up being needed. Did you at least have all your data backed up?

Should you need to reinstall, and since you're dual booting with Windows you need to be aware of this nasty bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You could try a few commands if you boot to Ubuntu and hit the black screen try entering a TTY using Ctrl+Alt+F1, then login as usual and try:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

```
sudo apt-get dist-upgrade
```

```
sudo dpkg --configure -a
```

You may need to repeat any of those commands in no particular order and the output may provide details regarding the current state of the system.

I would gladly try these commands that you have listed, but I am not sure that I can even get to a "terminal" to enter the commands.

When I turn on this computer, it will only boot as far as the words "Xubuntu 12.04".

Then stops booting. Nothing happens after that.

---

