---
title: "Boot Error : &quot;could not write bytes: Broken pipe&quot;"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by HARI_RAM_S on 2015-02-25
Hello guys!,
I am using ubuntu 12.04 LTS 64-bit, and I am not able to boot my laptop now which shows up the error message **could not write bytes: Broken pipe**. When I press the power button, manufacturer's logo is displayed which is immediately followed by this error message in a blank screen.
 I have no idea what's going on. But, I do remember what I did in my previous session, and are listed below.

I'm doing aosp project. So, I installed a few packages for ubuntu 12.04 as guided [here]("http://source.android.com/source/initializing.html"). But unfortunately, I had to install a few 32-bit pacages in my 64- bit system which is not possible by default. I can't use *dpkg --add-architecture *command, as it is not applicable for 12.04. So, I have to install ia32-libs(a 32-bit library) first before installing 32-bit packages.
So, I followed the instructions [here]("http://rumytaulu.com/2012/10/26/cant-install-ia32-libs-and-ia32-libs-multiarch-how-to-fix-it/") to install ia32-libs-multiarch and other 32 bit packages which are needed for me.

Then I, did the following in terminal.
[LIST]
[*]sudo apt-get update
[COLOR=#222222]sudo apt-get upgrade
[/COLOR][COLOR=#222222]sudo apt-get dist-upgrade[/COLOR]
[/LIST]
That's it!! Then I booted my lap which was left power-off for a few hours and that's where I begun to see this error message. I know, there will be a way around by logging in as root in recovery mode, but I have no idea after getting into recovery mode. Any help is appreciated.

Note: I saw somewhere that lack of disk space may be a reason. But I do have a lot of space.

---

