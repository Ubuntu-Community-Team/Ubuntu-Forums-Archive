---
title: "lubuntu 12.10 on ThinkPad T42p / Pentium M without PAE"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Master One on 2012-10-19
We still have a couple of pretty old but still usable ThinkPads with Pentium M processors without PAE here, which I am not willing to give up yet.

I just discovered, that from 12.10 there are no official 32bit non-PAE-kernels included any more, and no netboot non-pae/mini.iso image is provided, as it was for 12.04.

So is there any possibility, to get 12.10 onto a non-pae capable machine?

Can I install lubuntu 12.04 and upgrade to 12.10 keeping the non-pae kernel?

I can't believe that I am stuck now with 12.04 (which is no LTS for lubuntu) or forced to move to another distro now. :shock:

---

### Post by 2F4U on 2012-10-19
According to this mail, non-PAE CPU's are no longer supported in 12.10:

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035176.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035176.html)

I haven't checked, but there may be a PPA which provides such kernels.

I myself own a ThinkPad X31 and a T41 and, like you, are not willing to put in the trash. So I switched to Archlinux, because they provide non PAE kernels and at the moment don't seem to have an intention to stop this.

---

### Post by Master One on 2012-10-19
Sticking with lubuntu would be the easier way for me, so this is very disappointing!

The question is now, is there a PPA providing a recent non-pae kernel, and if there is, how would I proceed?

In the meantime I think I am going to try to install lubuntu 12.04 and try the upgrade to 12.10 to see what happens.

I played around with ArchLinux a lot in the past, but I gave up on Arch due to the often breakages.

Which alternatives to lubuntu 12.10 are else out there? I'd really like to have access to such a large software repository and have apt as the package manager.

---

### Post by kalehrl on 2012-10-19
I also have a machine with now notorious Intel Pentium M processor.
I am not even offered a chance to upgrade to 12.10.
In the past I have successfully upgraded my distribution but now this option is not present.
Maybe it is a built in safeguard against updating the distribution and then being left with a non booting system.

---

### Post by Zaruman on 2012-10-19
I think this "no more non-pae support" is very sad news. I allways thought the strength of linux distros was you don't have to have the latest hw available to use most of them. Atleast until today the hw has not been the broblem: with good hw you get very beautiful and top of the notch operating system but even if you don't have the latest hw the operating system is versatile and still working as charm.  :confused:

I have intel M based T40 laptop and I never have had any problems with the performance when using either l/x/ubuntu (fancy 3d disabled).

---

### Post by stafio on 2012-10-19
I have a Dell Dimension D600 laptop that has the Pentium M processor. Please see [my post here]("http://ubuntuforums.org/showthread.php?p=12305771") about getting 12.10 running on it.

---

### Post by Master One on 2012-10-20
Thanks stafio, so it is possible after all. All we need now is someone with the knowledge, time and a PPA to offer the latest 12.10 kernel without pae enabled, and we are set to go (there should not be a need to stay stuck with the 12.04 kernel).

Anyone?

---

### Post by webtomy on 2012-11-01
> **Master One said:**
> Thanks stafio, so it is possible after all. All we need now is someone with the knowledge, time and a PPA to offer the latest 12.10 kernel without pae enabled, and we are set to go (there should not be a need to stay stuck with the 12.04 kernel).

Anyone?

Hi, 

I don't want to put my T42 into trash, too. Therefore I've compiled a custom
kernel based on the latest 12.10 sources. 

The kernel runs stable (I've compiled the packages below with it :)) 

They are available under:

[http://bazaar.launchpad.net/~bj7u6139zdyf2a6nz2ly74oec10f2lnela24rsgd389d0elot5a7jz6hawymvsdk8c4sd6sr-bsln-jjcftv6wldnzq84cskygyvhqqb9qwjfcq0yfnwzcca0ux8ircw2a3om624q2ycdp941uw547/+junk/linux-image-i386-non-pae/files](http://bazaar.launchpad.net/~bj7u6139zdyf2a6nz2ly74oec10f2lnela24rsgd389d0elot5a7jz6hawymvsdk8c4sd6sr-bsln-jjcftv6wldnzq84cskygyvhqqb9qwjfcq0yfnwzcca0ux8ircw2a3om624q2ycdp941uw547/+junk/linux-image-i386-non-pae/files)

regards

Thomas

---

### Post by stafio on 2012-11-05
Hi Thomas,

Thanks for posting, but the link you have in your post is returning a Not found error.

---

### Post by turboscrew on 2012-11-06
It seems that most distros (Ubuntu-based Mint included) support non-PAE machines. The kernel approximates PAE with special segment limits.

I'm running Mint 13 / MATE in my IBM ThinkPad T42 (without "p").
Runs fine. My only annoyance is imprecise Synaptics TouchPad,
but I don't think that has anything to do with the kernel.

---

### Post by sudodus on 2013-05-11
Have a look at this wiki page, where you can test the new Lubuntu 13.04 fake-PAE, that can cooperate with most Pentíum M CPUs :smile:

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by tgalati4 on 2013-05-11
Don't be discouraged.  Only a small subset of Pentium M's really don't have PAE.  Many don't advertise PAE in *cat /proc/cpuinfo* and that causes the installer a problem.  If the installer can't find "pae" in /proc/cpuinfo, then it won't install.  But many Pentium M's will actually perform PAE and run just fine.  You just have to trick the installer.  Follow the link above and you should be good to go.

---

