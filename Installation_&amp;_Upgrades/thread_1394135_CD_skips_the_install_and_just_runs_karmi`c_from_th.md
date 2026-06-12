---
title: "CD skips the install and just runs karmi`c from the cd"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by Danwhelan on 2010-01-30
I'm trying to install on a new pc... quite old but OK...

I've made the latest 9.10 CD

This is what happens 

CD boots, I get the intro screen with the language selection (the first one) 

Menu options 

Try Ubuntu 
Install Ubuntu 
Check disc 
Test Mem 
Boot from hard disc 

When I click "install" it simply loads Ubuntu from the CD... which is fine... but I want to install it.. 

Help??

Dan

---

### Post by kansasnoob on 2010-01-30
After it boots to the live desktop what happens if you click on the "install Ubuntu" icon on the desktop?

---

### Post by Danwhelan on 2010-01-30
I don't think that there is one... although I'll have another look.

Last time it came up with the synaptic package installer... 

Should I nav back to the CD?

---

### Post by Danwhelan on 2010-01-30
I've found the install from here link... however it's slower than vista having a hard bad with a bad set of drivers and a virus  :-) 

Is there anyway to push it to skip the OS load and install right from the CD on boot??

Dan

---

### Post by darkod on 2010-01-30
Well, selecting the Install Ubuntu in the cd boot menu should start the install process and not load the live desktop. But you said for you it just loads the live desktop.

I have no idea why would it do that. Maybe try with creating bootable usb stick and use that, to make sure you have no problems with the optical drive or something.

---

### Post by Danwhelan on 2010-01-30
I'm trying to bring an ACER travelmate back from the dead - the USB boot is not an option really unless you are a bios expert... :-) 

It's annoying as up until the last three or so weeks my experience with Ubuntu has been just shy of perfect... 

:-(

---

### Post by darkod on 2010-01-30
Depending what you mean by "dead". The thing is, ubuntu is designed to load the live desktop if you cancel the install process for example.
So I'm just assuming here, but lets say it can't detect any hdd, would it also load the live desktop right away without giving you options to install because it thinks you have nowhere to install to?

---

### Post by Danwhelan on 2010-01-30
Oh no... bring it back from the dead I mean that at the moment it's running xp pro. 

The machine is fine... and ubuntu loads fine... just very slow

---

### Post by markbuntu on 2010-01-30
Well, it is running from a cd which is a very slow way to go. Did you use the check disk for defects option. You should do that, the disk may have problems/errors if it will not go to install from the menu.

---

### Post by oldos2er on 2010-01-30
FWIW, I've never seen any difference between 'Try Ubuntu' and 'Install Ubuntu'. They both should take you to a GUI desktop with an 'Install Ubuntu' icon showing.

---

### Post by Danwhelan on 2010-01-30
Thanks... 

But have a look at 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

It's that welcome page I'm missing 

Dan

---

### Post by jaschallies on 2010-01-30
I have the same problem, will not install from CD or installation icon on desktop. Installed FEDORA with no problems ????

---

### Post by rickc1970 on 2010-01-30
You either have a problem with the CD or the CD rom. At least that is my guess. When I installed mine yesterday it would quit installing halfway through and goto the live cd. I apparently had scratched the disk as that disk had worked before. I went and downloaded 9.10 and burned that to a new cd and it worked. 

If you have an Acer you might want to hit F2 at startup to get to the BIOS screen and then you can see what order your dives boot up. make sure it is trying to boot from the CD first. 

I'm not saying you have a scratched cd definately. it could just be some data that it can't read for some reason.

---

### Post by djchandler on 2010-01-30
> **jaschallies said:**
> I have the same problem, will not install from CD or installation icon on desktop. Installed FEDORA with no problems ????

Please re-boot the CD and select option "Check CD for Defects."

---

### Post by jaschallies on 2010-01-30
OK, tried to install on second PC and it does the same thing, CD might be faulty or the download....

---

### Post by jaschallies on 2010-01-30
Ran check on cd, found errors in 1 file, does this now mean that I have to download it again??

---

### Post by jaschallies on 2010-01-30
Burnt new cd, all working ok now, thanks

---

### Post by djchandler on 2010-01-30
> Ran check on cd, found errors in 1 file, does this now mean that I have to download it again?

Not necessarily. The problem could be the burner. Did you check the md5 sum? You only need to check the the correct md5sum (IMHO) string against the .iso image you downloaded. The data strings came from the repository hosted by Argonne National Laboratory Public Software Mirror. sha1sums and sha256sums are data strings for other methods of testing data integrity. Some people don't trust MD5. Theoretically the sha256 method is more thorough.

If the md5 sum matches your downloaded .iso file, try a different CD burner. It's possible you may need to replace the burner/reader in the computer you are trying to install with. If it's faulty burning, it could be faulty reading too due to an alignment problem. It's cheaper and easier to replace than to fix.

[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

```
Here are the md5sums:

836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe

sha1sums:

3e8dfc4d8d43903f17fb09f0e1113652a788651a *ubuntu-9.10-alternate-amd64.iso
45cce271d704d200bea0cfca9306125bc46fa623 *ubuntu-9.10-alternate-i386.iso
56c7265192c857963f305cd5edaef5af536d3c92 *ubuntu-9.10-desktop-amd64.iso
5cd81c444ce819005cc39e6d899e02e16043cd02 *ubuntu-9.10-desktop-armel+dove.img
ec19ea00e6fe6eed820242ac8d998135bb63d293 *ubuntu-9.10-desktop-armel+imx51.img
2816a96de299631e545d1c068837d05c64157e49 *ubuntu-9.10-desktop-i386.iso
42cf7e24a2f63bb73163dc84e35f79a42344ee21 *ubuntu-9.10-netbook-remix-i386.iso
f077498d6a88820905d296177863ca3b5a32f529 *ubuntu-9.10-server-amd64.iso
717bd8c9c6b2a664beac51679c57fde3d23d6e93 *ubuntu-9.10-server-i386.iso
0aca801d3d6b892d4ad51aebae9e233f414f11d8 *wubi.exe

sha256sums:

18d38fede3cf82f765bf6ae02ba52c8db691ba266a400c437a4fe9b3f7581ac5 *ubuntu-9.10-alternate-amd64.iso
0547d90cf3586a6a7b810fd4d574645fe078451427abe520145dcad05fe3ee4d *ubuntu-9.10-alternate-i386.iso
a3f9c534e005729fbed3856239b1ec3341fef8d0d20c1d92aab2bcf844985eee *ubuntu-9.10-desktop-amd64.iso
5f71417a2446b6273b07295cee17f78d708f98064f964582727548fc974c82bd *ubuntu-9.10-desktop-armel+dove.img
20e0d25801d9e466c8b7606666137e5be156fa467bfb40780e0cd0366f7facf9 *ubuntu-9.10-desktop-armel+imx51.img
d36a4c3d9eb296471d21c0c07cd1bbe467c9f5de62dd19cbd6ac762bfa19bfaf *ubuntu-9.10-desktop-i386.iso
b56f09f1a2ddcf64cb03bab12492504ce93334a47aadc73ab76f12ebdb06dadf *ubuntu-9.10-netbook-remix-i386.iso
9a0c681bbf31c4e9f9cd1d2541c9cb80bffc3ed3816755b79d5167a7296f9a7f *ubuntu-9.10-server-amd64.iso
23c5422bbbf691111257bdaf01a373b1114174102bf3b2c3aa26e3737eb4e76b *ubuntu-9.10-server-i386.iso
168070ed84aebb7cf2b99de12ac8ad648ede9588416e168bff6f30e8fb48948f *wubi.exe
```

---

### Post by Danwhelan on 2010-01-30
Wow 

I'm sorry - I know that you are trying to help... but this is why people are scared to change to Ubuntu

56aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe

sha1sums:

3e8dfc4d8d43903f17fb09f0e1113652a788651a *ubuntu-9.10-alternate-amd64.iso
45cce271d704d200bea0cfca9306125bc46fa623 *ubuntu-9.10-alternate-i386.iso
56c7265192c857963f305cd5edaef5af536d3c92 *ubuntu-9.10-desktop-amd64.iso
5cd81c444ce819005cc39e6d899e02e16043cd02 *ubuntu-9.10-desktop-armel+dove.img
ec19ea00e6fe6eed820242ac8d998135bb63d293 *ubuntu-9.10-desktop-armel+imx51.img
2816a96de299631e545d1c068837d05c64157e49 *ubuntu-9.10-desktop-i386.iso
42cf7e24a2f63bb73163dc84e35f79a42344ee21 *ubuntu-9.10-netbook-remix-i386.iso
f077498d6a88820905d296177863ca3b5a32f529 *ubuntu-9.10-server-amd64.iso
717bd8c9c6b2a664beac51679c57fde3d23d6e93 *ubuntu-9.10-server-i386.iso
0aca801d3d6b892d4ad51aebae9e233f414f11d8 *wubi.exe

---

### Post by Danwhelan on 2010-01-30
Jaschillies 

Try the lite version... 

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

It looks like major sudo apt get stuff, but in fact is quite simple... 

Good luck !!!!

Dan

---

### Post by oldos2er on 2010-01-30
> **Danwhelan said:**
> Wow 

I'm sorry - I know that you are trying to help... but this is why people are scared to change to Ubuntu


??

 There shouldn't be anything scary about md5sum; it's available on Windows as well as *nix. See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by djchandler on 2010-01-30
> **Danwhelan said:**
> Wow 

I'm sorry - I know that you are trying to help... but this is why people are scared to change to Ubuntu


If they are scared of md5 sums or sha1 sums, then they probably shouldn't be downloading software from the internet and running it on their computers, no matter what operating system they are running.

I explained that that there was only one string out of all those posted to compare against, the one matching the download and what checksum software was available.

Not knowing how much bandwidth jaschallies has available, it seems a reasonable alternative to downloading an almost 700MB .iso image over again once jaschallies discovered it was a bad CD.

Do md5 or sha2 checksums scare you? How is explaining the necessity of checking the integrity of an internet download scary? No mater what operating system one uses, it's simply a matter of good common sense everyday secure practice.

---

