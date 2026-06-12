---
title: "[lubuntu]External monitor output issues after update"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by michael_brown2 on 2016-05-19
Hi guys

I'm currently running Lubuntu 16.04 on an ASUS EEEPC R101 and trying to output to a LG flatron L1732S monitor.

Back when Lubuntu version 15.10 was still current, the monitor worked fine for a while, until a particular update came along (it wasn't the upgrade to 16.04). At that point my monitor ceased to work. I tested the monitor with another computer and it worked fine, so there's nothing wrong with that. I reinstalled version 15.10 via a clean iso install, without any updates, and the monitor worked fine again. Then I re-ran the updates (still, 16.04 wasn't out yet) and the monitor stopped working again. Of course, I've upgraded to version 16.04 since then and the monitor still isn't working. I've tried downloading another monitor settings program (gddccontrol) and I get the following results:

[ATTACH=CONFIG]269155[/ATTACH]
My monitor only has one physical port and that's the VGA input. I'd swtich the current monitor to the only other available option and see the following
[ATTACH=CONFIG]269156[/ATTACH]
I tried running the suggested command and got the following output:
"
ddccontrol version 0.4.2
Copyright 2004-2005 Oleg I. Vdovikin (oleg@cs.msu.su)
Copyright 2004-2006 Nicolas Boichat (nicolas@boichat.ch)
This program comes with ABSOLUTELY NO WARRANTY.
You may redistribute copies of this program under the terms of the GNU General Public License.

Probing for available monitors......
Detected monitors :
No monitor supporting DDC/CI available.
If your graphics card need it, please check all the required kernel modules are loaded (i2c-dev, and your framebuffer driver).
"
I sent that off to the suggested email address, so I'll see what comes of that. I'd hit ok back on gddccontol and get the following:
[ATTACH=CONFIG]269157[/ATTACH]
I don't know what happened in that previous update during the life of version 15.10 to stop my monitor from working, but it would be really nice if it could either be fixed in a new update, or, failing that, could you guys please possibly let me know about a way that I could fix this?

Thanks
michael_brown2

---

### Post by sudodus on 2016-05-19
I think there is Intel graphics in your eeePC. There is a known issue, that can be fixed by installing a package (and rebooting). See this link

[Lubuntu 16.04 flashing cursor with certain Intel video drivers](http://ubuntuforums.org/showthread.php?t=2321734)

This package also made it work with an external monitor.

```
sudo apt-get install xserver-xorg-video-intel
```

Good luck :-)

---

### Post by michael_brown2 on 2016-05-20
I have now installed 'xserver-xorg-video-intel' and 'xserver-xorg-video-intel-dbg' via the synaptic package manager and rebooted, as per post #3 of the thread you gave, however there is no change. I still can't get external monitor ouput via either tools that I mentioned above. The other methods described in that thread weren't ideal for me, as I don't really want to run xubuntu and the UXA method doesn't look like it's going to give me optimal display results and possibly not even external output.

---

### Post by sudodus on 2016-05-20
I agree that UXA is not a good solution. I have no other tip to offer with 16.04 LTS, so I hope someone else will chip in a suggest another solution.

It might continue to work after updating/dist-upgrading (with an up to date system), if you try with the still supported version ***14.04.1 LTS*** with the Trusty kernel series, 3.13.

---

### Post by michael_brown2 on 2016-05-24
Had a problem trying this solution. I installed 14.04.1 via clean iso install. The external monitor worked fine straight after the install. I ran an update (not a distro upgrade) and the monitor still worked fine. I tried an upgrade to version 15.10 and as the upgrade came near completion (it had finished getting new packages and was almost finished installing the packages), the whole system crashed. I lost the gui and all I had was a black screen with a flashing underscore cursor (I couldn't even type anything). Would installing xserver-xorg-video-intel and xserver-xorg-video-intel-dbg before update/upgrade help here?

[COLOR=#000000]Also, how do I edit the original post to have a lubuntu tag (it only has a lubuntu prefix)? I couldn't find that feature while trying to edit the OP.

Edit: I forgot to say that the OS would fail to boot after the crash. I'd just get a TUI saying a bunch of things including something to do with "Kernel Panic".
[/COLOR]

---

### Post by sudodus on 2016-05-24
It is better idea to stay with 14.04.1 LTS and update/dist-upgrade (staying with the Trusty kernel series, 3.13). This version of Lubuntu will live until April 2017, while 15.10 will reach end of life in July 2016 (very soon, 9 months after its release). And it will be more likely to continue working with an external monitor too.

In April 2017 the Xenial version 16.04 LTS has been released for one year and will probably be very debugged and polished. It is possible that it will work with an external monitor.

-o-

You can get help from the moderators by pressing the 'Report Post' button at the bottom right corner (of the post). Then you get an edit box, where you write what you want them to help you do. So that button can be used not only to report abuse, but also to get help with editing your own posts (administration and forum tasks - not help to solve technical problems with the Ubuntu family operating systems).

---

### Post by QDR06VV9 on 2016-05-24
> **michael_brown2 said:**
> 
[COLOR=#000000]Also, how do I edit the original post to have a lubuntu tag (it only has a lubuntu prefix)? I couldn't find that feature while trying to edit the OP.
[/COLOR]
Done! I have Edited the thread title as requested.

---

### Post by michael_brown2 on 2016-05-25
runrickus: Thanks for that.

Sudodus: I thought that by dist-upgrading you meant upgrade to version 16.04 from 14.04.1. I was trying to do this simply by repeatedly applying the software updater to update/upgrade incrementally (I was trying to upgrade to 15.10 as a step towards upgrading to 16.04). Wouldn't leaving the version at 14.04.1 give me security risks?

---

### Post by sudodus on 2016-05-25
The version 14.04.1 LTS with the Trusty kernel will receive updates/upgrades including security fixes until the end of life of each of the family flavours.

Standard Ubuntu (with Unity) and Ubuntu Server have 5 years of support, so until April 2019. I think all the other flavours (Kubuntu, Lubuntu ... Xubuntu) have 3 years of support, so until April 2017. I know that Lubuntu has 3 years of support.

The main difference is that the program packages that are specific for these other flavours have shorter support time, while the common program packages have 5 years of support.

---

### Post by sudodus on 2016-05-25
```
sudo apt-get update && sudo apt-get dist-upgrade
``` upgrades program packages within the same kernel series. See ```
man apt-get
```


```
sudo do-release-upgrade
``` upgrades from one version alias release to the next one, or skips directly from one LTS release to the next LTS release.

---

### Post by michael_brown2 on 2016-06-03
sudous: I tried reinstalling 14.04.1 via iso and trying your latest suggestion. Running "sudo apt-get update && sudo apt-get dist-upgrade" updated 7 packages, however running "sudo do-release-upgrade" returned an error. Here's a screenshot:
[ATTACH=CONFIG]269416[/ATTACH]
I know I had a working internet connection, as I tested it before running the command (I did so via two separate internet connections at two separate times). Perhaps the server isn't working to update directly from version 14.04.1 to version 16.04?

Michael_brown2

---

### Post by sudodus on 2016-06-03
Why are there wily-backports?

Are you release-upgrading from trusty to xenial? In that case wily should not be involved. Maybe the upgrade works better if you remove all PPAs and all non-standard repositories.

---

### Post by michael_brown2 on 2016-06-23
Edit: I forgot to say originally that it turns out that I accidentally tried to install an alternate version of 14.04.1. Now, running the standard version I got the following results:

It took me a while to finally get around to properly doing this, but it mostly worked. The external monitor is working and I updated the software via the Software Updater and by using 
"sudo apt-get update && sudo apt-get dist-upgrade", however when I try to run "sudo do-release-upgrade" it just says "No new release found", which is strange. It's no big deal, because my problem is fixed and 14.04.1 is workable, but it would have been nice to directly upgrade to 16.04.

Anyway, thanks for your help.

---

### Post by QDR06VV9 on 2016-06-23
You will not be notified of an upgrade to 16.04 until the first point release Due July 21st 2016.

---

