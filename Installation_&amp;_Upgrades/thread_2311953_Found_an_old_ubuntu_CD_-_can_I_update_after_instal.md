---
title: "Found an old ubuntu CD - can I update after installation?"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by helm10101 on 2016-01-31
I found an old 14.01 Ubuntu LTS, and I see that now it's 14.03 LTS.
Is it possible to install the 14.01 and then update to 14.03 through Ubuntu itself?

Thanks

---

### Post by sammiev on 2016-01-31
> **helm10101 said:**
> I found an old 14.01 Ubuntu LTS, and I see that now it's 14.03 LTS.
Is it possible to install the 14.01 and then update to 14.03 through Ubuntu itself?

Thanks

Hi and Welcome,

Yes you can update or if you have a DVD/USB you can download the latest 14.03 LTS and install from there.

Always best to try it live first from the DVD/USB before installing to see how it reacts to your hardware.

Either way your good to go.

---

### Post by helm10101 on 2016-01-31
> **sammiev said:**
> Hi and Welcome,

Yes you can update or if you have a DVD/USB you can download the latest 14.03 LTS and install from there.

Always best to try it live first from the DVD/USB before installing to see how it reacts to your hardware.

Either way your good to go.

Thank you!
I just can't find a USB stick or an empty DVD right now :p
So after I install the 14.01, how do I update Ubuntu to the latest version inside Ubuntu?

---

### Post by sammiev on 2016-01-31
> **helm10101 said:**
> Thank you!
I just can't find a USB stick or an empty DVD right now :p
So after I install the 14.01, how do I update Ubuntu to the latest version inside Ubuntu?

The software will ask you if you would like to update while installing or you can and should either way check for updates after the install.

It's called "Software Updater"

---

### Post by deadflowr on 2016-01-31
Install and simply run an update.
I assume since there is no 14.01, you mean 14.04.
And the latest for that release is 14.04.3.
Updating will bring you in line with 14.04.3. --sans no upgraded hardware stack.

But...
Unless you want the heartache that can come with trying to upgrade the hardware stack, stick with the disk you have, 
and simply run the software updater.

If you did want to upgrade to the 14.04.3 hardware stack, you can do so by installing the hardware stack.
Run this:
```
sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid 
```
Buyer beware, and note it is probably not worth it to do, anyway.

Quick reference from here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

And really, the hardware stack is the only difference between 14.04 and 14.04.3.
All other software packages are the same.

So there is little added benefit, unless you have new hardware.
New as in it was released publicly after 14.04 was release in April 2014.
Not new as in new to you.

---

### Post by lisati on 2016-01-31
> **helm10101 said:**
> I found an old 14.01 Ubuntu LTS, and I see that now it's 14.03 LTS.
Welcome to the forum.

Do you mean 14.04.3? If so, you should be able to update to a newer version without too many hassles.

---

### Post by QIII on 2016-01-31
I'd almost recommend against the HWE unless you have some fairly new hardware that you want open source support for.

HWE stacks can have dates of end of support that do not quite align with the releases and you have to be aware of how to deal with that.

Just update, dist-upgrade and maybe pull in the vivid kernel if you want.

---

### Post by steveo314 on 2016-01-31
Installing from the disc will get you 14.04.01 and after that running 'sudo apt-get update && apt-get dist-upgrade' will put you at 14.04.03, which is just the newest iso image of 14.04. The only issues will come when you change the release name in the sources list to a newer or newest or beta release.

---

### Post by helm10101 on 2016-01-31
Thanks everyone!
I did have a mistake: I meant that I found a 14.04.1 DVD and that the current version is 14.04.3 :KS

> **deadflowr said:**
> Install and simply run an update.

Updating will bring you in line with 14.04.3. --sans no upgraded hardware stack.

But...
Unless you want the heartache that can come with trying to upgrade the hardware stack, stick with the disk you have, 
and simply run the software updater.

If you did want to upgrade to the 14.04.3 hardware stack, you can do so by installing the hardware stack.
Run this:
```
sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid 
```


So if I get it correctly: If I now download a new Ubuntu to a USB/DVD instead of using my current old DVD, I will automatically get this "hardware stack" (which I don't know what that is really :p, but I will read about it after posting this), but if i Install my old DVD and update, I won't really have to do that?

> **steveo314 said:**
> Installing from the disc will get you 14.04.01 and after that running 'sudo apt-get update && apt-get dist-upgrade' will put you at 14.04.03, which is just the newest iso image of 14.04. The only issues will come when you change the release name in the sources list to a newer or newest or beta release.

I am no expert in Linux, what exactly is the release name in the sources list? When might I encounter this? I can fix that?
And, is there a graphical software updater? or sudo is the only way? (Maybe through System Settings?)

Thanks again!

---

### Post by grahammechanical on 2016-01-31
> And, is there a graphical software updater? or sudo is the only way? (Maybe through System Settings?)

There is most certainly a graphical updater. It is called Software Updater. It does it all with a couple of clicks. Ubuntu 14.04 is what we call a Long Term Support (LTS) version. It gets five years support with security fixes. To keep the LTS version up to date with the latest improvements made to the Linux kernel and hardware modules which in turn keep Linux up to date with the latest hardware, The LTS version gets point releases every six months or so for about 2 years.

This is why the latest version is 16.04.3. On 11th February point release number 4 will be out (14.04.4). If you download the ISO image then you will get 14.04.4 without any need to upgrade or worry about kernels and hardware enablement stacks. It is just a thought.

At the end of April this year the next LTS version will be released (16.04). Software Updater will nag you about upgrading. It is just a click away. Or you can ignore it and the nagging will stop but you can still upgrade to 16.04 during the next 3 years before support for 14.04 ends.

Regards.

---

### Post by oldfred on 2016-01-31
In effect there are two versions that will say they are 14.04.3.
I have the original installed 14.04 and it still has the original kernel and other support software.
The newer versions if directly installed get the newer kernels to support newer software, but have to continue to be udpates as they are the HWE or hardware enablement stack (new kernels from newer versions).

But even though I have the older original 14.04, with its normally updates it says it is 14.04.03, but just does not have newer kernel.

If using an older version, be very careful on a reinstall. There is a major bug and the only safe way to reinstall is with Something Else. And auto reinstall option may erase entire hard drive even if saying it is only updating/replacing Ubuntu.

---

### Post by steveo314 on 2016-01-31
When I say release names, 14.04 is Trusty Tahr, 15.10 is Wily Werewolf, 6.06 was Dapper Drake. So say you install 14.04 from that disc. The release name in your sources list file is trusty. If you were to change it to wily or xenial and run a dist-upgrade there is a strong chance you may have some issues when packages get updated, removed, or added. It's always safer with Ubuntu to use a disc for each release and do a fresh install to a newer version. With you wanting to stay with 14.04 there won't be any issues with upgrading. You could installed the 14.04.03 kernel or stay with the 14.04.01 kernel.

---

### Post by helm10101 on 2016-02-01
Thanks everyone.
So installing an older version and updating through the PC, will not update the Linux Kernel if I get it right?
And, it might cause some problems later on.

But if installing an older version and updating without getting kernel update, what's the point? :D
Also, I'm just curious: If every latest stable version is LTS, why do they mention it? Is it because some people prefer to stay at older versions?

---

### Post by oldfred on 2016-02-01
Some want to install the LTS on newer hardware that the older kernel & support software do not support. 
But if you have installed the original LTS version and it works with your hardware, there is no reason to upgrade kernel. Just update security fixes and usually other updates, but you do not get newer versions of software, except Firefox and maybe a couple of others. 

You have to install the newest release to get both kernel and latest versions of all software.
I typically have the LTS as my main working system on SSD and have a current version of Ubuntu on HDD just to see what has changed.

---

### Post by Bucky Ball on 2016-02-01
I think your best bet is to plug in an ethernet cable, boot from the 14.04.1 disk, choose 'Try Ubuntu' and have a look around. You might get a lot of your questions answered quickly and have new ones when you are actually working in and experimenting with the environment. If all looks good, simply hit the install icon on the desktop.

It is generally best not to install third-party drivers or updates during the install. They have the potential to mess things so you start off having to fix stuff. If you use the Software Updater once the machine is installed you have a better chance of tracing what broke, if anything does. You can also add third-party apps then and easier to identify and remove if they break something.

Ubuntu LTS releases have five years support, everything else three. LTS is generally very stable and great for production environments or any environment where breakage is not acceptable. Many users have a 'main squeeze' LTS and use the other releases in as a virtual machine or install on another partition. I generally start fooling around with the next LTS on another partition a month or so prior to its release and migrate over when I'm satisfied it is fairly rock solid after it is released.

Good luck. :)

PS: 14.04 LTS hasn't reached middle age yet, is the newest supported LTS (12.04 LTS is also still supported) so not old. Another three years and two months support to go! It is quite valid to be using 14.04.1 or 14.04.4 or 12.04 LTS for that matter. Whatever suits the circumstances.

---

### Post by kansasnoob on 2016-02-01
> **helm10101 said:**
> Thanks everyone.
So installing an older version and updating through the PC, will not update the Linux Kernel if I get it right?
And, it might cause some problems later on.

But if installing an older version and updating without getting kernel update, what's the point? :D
Also, I'm just curious: If every latest stable version is LTS, why do they mention it? Is it because some people prefer to stay at older versions?

You still seem to be confused about LTS HWE kernel support:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

As you can see there 14.04 (Trusty) has 5 point releases. Both the original 14.04 and 14.04.1 installation images will give you the 3.13 series kernel which will receive bug fixes and security updates clear up until April 2019. Installations performed with 14.04.2, 14.04.3, and 14.04.4 images will give you the previous interim releases kernel series but they all reach HWE EOL much sooner requiring a somewhat major kernel series and X-stack upgrade. I recently posted more about that here:

[http://ubuntuforums.org/showthread.php?t=2310398&page=4&p=13429075#post13429075](http://ubuntuforums.org/showthread.php?t=2310398&page=4&p=13429075#post13429075)

So when you say "it might cause some problems later on" in actuality if the original Trusty kernel series works OK on your hardware you're less likely to encounter major problems than if you install using the 14.04.2, 14.04.3, or 14.04.4 images. The one exception is this nasty installer bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Please remember also that we're only talking about LTS versions. The normal (or interim) releases have a much shorter (9 month) support cycle:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by helm10101 on 2016-02-01
I just found out it's actually 14.04.02 and not .01 :). So I will have HWE anyway :)

But the thing I still don't get now is: Using software updater will update the software only but leave me with the current installation kernel? Or it will also update kernel to the latest version?

---

### Post by steveo314 on 2016-02-01
The update won't install the newest kernel automatically. But you can choose to install it afterwards if you desire.

> **helm10101 said:**
> Thanks everyone.
So installing an older version and updating through the PC, will not update the Linux Kernel if I get it right?
And, it might cause some problems later on.

But if installing an older version and updating without getting kernel update, what's the point? :D
Also, I'm just curious: If every latest stable version is LTS, why do they mention it? Is it because some people prefer to stay at older versions?

Every stable release isn't an LTS. They're doing the LTSs every 4th stable release. 6.06, 8.04,12.04,14.04,16.04,..... 
6.06 was the only Ubuntu not released on time. It was the first LTS,Long Term Support, and also got the nickname '_L_ate _T_o _S_hip'.

---

### Post by kansasnoob on 2016-02-01
> **helm10101 said:**
> I just found out it's actually 14.04.02 and not .01 :). So I will have HWE anyway :)

But the thing I still don't get now is: Using software updater will update the software only but leave me with the current installation kernel? Or it will also update kernel to the latest version?

If you install with 14.04.2 media you'll get a HWE EOL notification around August of this year and you'll need to perform the HWE upgrade offered by the Software Updater to keep receiving kernel updates. That will upgrade you to the Xenial series kernel.

---

### Post by Bucky Ball on 2016-02-01
LTS releases are supported for five years, all other for nine months. There is a release every six months, April (04) and October (10). Therefore, 14.04 LTS = April, 2014.

---

### Post by helm10101 on 2016-02-04
Thanks, you made it more clear :). I ended up installing 15.10

---

