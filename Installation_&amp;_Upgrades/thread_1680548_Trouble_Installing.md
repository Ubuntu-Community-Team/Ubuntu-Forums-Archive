---
title: "Trouble Installing"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by Szat on 2011-02-02
Hello All,
  I have recently received my new [netbook]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220850") and am having trouble installing Ubuntu Netbook 10.10.  I have also tried installing Ubuntu Desktop 10.10 with no luck.  I have never had trouble installing Ubuntu in the past, but this is the first time I'm using a bootable USB drive. I followed the instructions for creating one using Universal USB Installer, but there is a SysLinux error (others have the same problem). I am now trying to install Ubuntu Netbook with a bootable USB made with Unetbootin. It seems to be working better, but after 20 minutes it is still "thinking" at the Preparing to install Ubuntu-Netbook step. This is just after the Select your language page. When I say "thinking" I mean Ubuntu's version of the hourglass and not my hdd or my usb (has an LED). Any suggestions? By the way my system came with crappy Windows 7 Starter that I would rather have not had to begin with.  Thanks for the help, it is much appreciated!

When I cancel the installation I briefly see an error message that says: glib warning failed due to unknown user id (0). I can't make out the entire message though.

---

### Post by Szat on 2011-02-02
bump

---

### Post by Quackers on 2011-02-02
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, whilst booting from the live usb you should see the first purple screen (with a little man graphic at the bottom of the screen). At this screen press any key. Then choose your language and on the next screen you will see some options. Choose the one that checks the cd for errors (don't worry about not using a cd, it's the same thing with a usb). If any errors are reported, try burning the image to usb again.

---

### Post by Szat on 2011-02-05
Hello, I looked up the md5sum file in the installer files and this is what it shows:

27cfb218196cea72593d207de0cb30a2  ./casper/initrd.lz
1e589beafec41851ac302ea8868eb6c9  ./casper/filesystem.manifest
da63997001eae0649d6320a5a732000a  ./casper/filesystem.manifest-desktop
2411b880b689c5e5611f2075a36a88e4  ./casper/filesystem.squashfs
50065155d2b4c37740b0e123cbfebc43  ./casper/vmlinuz
9c4ff58b0ef6205f64bfb50babaa4be4  ./casper/filesystem.size
71285e5fbba953d263aa8e2a6fd2b710  ./dists/maverick/Release
5a9313d8543fea359656a1b08b411461  ./dists/maverick/restricted/binary-i386/Packages.gz
2f88764d78ab5a3101c5ed72f7f79d6c  ./dists/maverick/restricted/binary-i386/Release
946e27fad8731369988e06fa4b230234  ./dists/maverick/Release.gpg
47bbffb8aeab415001720703be6e7852  ./dists/maverick/main/binary-i386/Packages.gz
b073e6f461e2d54143f70b3d40f57636  ./dists/maverick/main/binary-i386/Release
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
cb76c0736df486bb167b8ee1249ebdb8  ./.disk/casper-uuid-generic
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
28858a611c4058993f34987e34f14a9d  ./.disk/info
3ede15b272201485ddba0561a5eb06cb  ./autorun.inf
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm
5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
597df07bd94c2844aade36c28a7d421f  ./install/mt86plus
fe6fa04c981a9d3835f12f27bd6dda71  ./usb-creator.exe
2c34f6dff899c20691f43e5d63fc438c  ./preseed/ubuntu-netbook.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
6b711ba074b35f57ff4cb4c453109709  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
d21ce544f70c9c7d6a3af452d3e4b7c3  ./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20100718-2_i386.deb
e8db25137962d97309baf051a7e66f7b  ./pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb
1cb737e6d019f35cc5e4664e5b5db265  ./pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-3_i386.deb
74524f0ecc162d0f89f999ef832c99aa  ./pool/main/n/ndiswrapper/ndiswrapper-common_1.56-3_all.deb
561b1be68e99e1c7c9e6664fb6e87e81  ./pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-1_all.deb
5cf3364130a9e9b11d71deadb0354648  ./pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-1_all.deb
96e9bf35608b3380ca8dc6920255de3b  ./pool/main/b/build-essential/build-essential_11.5_i386.deb
a3279e18d400c54047b49853462d02b4  ./pool/main/b/b43-fwcutter/b43-fwcutter_013-2_i386.deb
cd2a372886afc02ce646fcb1c1baf753  ./pool/main/b/binutils/binutils_2.20.51.20100908-0ubuntu2_i386.deb
3b4bb5a8f62636fd45480eecbe0520ea  ./pool/main/d/dpkg/dpkg-dev_1.15.8.4ubuntu3_all.deb
0708808b66daffa5520d270d76151417  ./pool/main/d/dpkg/libdpkg-perl_1.15.8.4ubuntu3_all.deb
619e1816e9921cf3c2dbabce1f305341  ./pool/main/d/dict-xh/myspell-xh_20070206-4_all.deb
bd0c1ef87e2466d74ea6ac42755ea29e  ./pool/main/d/dkms/dkms_2.1.1.2-3ubuntu1_all.deb
69ae325f1d7a922ad3444e7b29fcb1fe  ./pool/main/g/gcc-4.4/gcc-4.4_4.4.4-14ubuntu5_i386.deb
67259128a0d7c83e7c7b56e270a0741e  ./pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.4-14ubuntu5_i386.deb
09411ea75687bac8174dc18c65570547  ./pool/main/g/gcc-4.4/g++-4.4_4.4.4-14ubuntu5_i386.deb
c9e8496b8813bea01690da7b43cc7bb9  ./pool/main/g/gcc-defaults/gcc_4.4.4-1ubuntu2_i386.deb
4e3190bd7e336e9640cc643118e43a2b  ./pool/main/g/gcc-defaults/g++_4.4.4-1ubuntu2_i386.deb
308563b2eb5f6a64ead0a3b81afa4c66  ./pool/main/u/ubiquity/oem-config_2.4.8_all.deb
4a868215dc22264a78983d70fb9f73d6  ./pool/main/u/ubiquity/oem-config-gtk_2.4.8_all.deb
cd0e6b018315379a3ebf018dc6416556  ./pool/main/m/manpages/manpages-dev_3.24-1ubuntu1_all.deb
f8b821c5b94f3f06c779124959a47db2  ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu7_i386.deb
b745dbd9de222dd67df6b1fef0cd0c76  ./pool/main/w/wspanish/wspanish_1.0.25_all.deb
6fb4010fefb48765c5267432a6240cf4  ./pool/main/e/espa-nol/myspell-es_1.10-9_all.deb
1500f991998916ecdd4eb127366e27c4  ./pool/main/e/eglibc/libc-dev-bin_2.12.1-0ubuntu6_i386.deb
539bab61fcb1d3672d13888395ec45d9  ./pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu6_i386.deb
4d4d776758c9d1535b486000ff673eff  ./pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
80ca9c983f402d6dddb02c4d7c1b27c4  ./pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
90728e63cba4cbc65d0d653ab400d164  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_i386.deb
3aafaec3951819c3e353e6fd635bc289  ./pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb
f4b1c562a7e3dad81774e8420d731845  ./pool/main/l/language-support-writing-es/language-support-writing-es_10.04+20100311_all.deb
7e726b5a5bd077620c21e4ee2c535a84  ./pool/main/l/language-support-es/language-support-es_9.10+20090909_all.deb
67169557c4c6fe5ea454057af102a8e4  ./pool/main/l/lupin/lupin-support_0.32_all.deb
0a0a633061af8b8027b207c5497a1841  ./pool/main/l/language-support-xh/language-support-xh_9.10+20090909_all.deb
18086577a1b04386a8d1c6685331078c  ./pool/main/l/language-support-writing-xh/language-support-writing-xh_9.10+20090909_all.deb
4a81f4fcb3dac9591e4147685840bb3d  ./pool/main/l/linux/linux-libc-dev_2.6.35-1022.33_i386.deb
cb3d5b5de9f45e5a107131c7230679f9  ./pool/main/s/setserial/setserial_2.17-45.2ubuntu2_i386.deb
fb14d53b17b5317d301ae804af519b8a  ./boot/grub/loopback.cfg
d1db1f93bb7486593b7d1ea023c0e3f8  ./wubi.exe
1a066140507c1cf5a0150879151a10d7  ./README.diskdefines

I see the ubuntu-10.10-netbook-i386.iso md5 sum is supposed to be: 6877bf8d673b87ba9500b0ff879091d0
This sum is not in the file. I downloaded this .iso from the Ubuntu netbook website.
However, when I used the md5sum program for Windows it matched up correctly! Any advice?

---

### Post by kansasnoob on 2011-02-05
> when I used the md5sum program for Windows it matched up correctly! Any advice?

When first booting the Live USB irght after the system/BIOS screen passes you'll see a purple screen with two small icons at the bottom. At that point you have 3 seconds to press any key (I just use Enter), and then you'll see the screen to select language followed by a screen with 5 options, select Check CD for defects.

NOTE: I know this is a Live USB but the CD image is still used.

That usually takes about 4 minutes to complete and should say "no defects found". If that passes we need to examine your hardware specs so please post the netbook model and anything else you know about it.

---

### Post by kansasnoob on 2011-02-05
I just noticed you included a link to Newegg. I'll have a look.

---

### Post by kansasnoob on 2011-02-05
I wonder if this might be helpful:

[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

---

### Post by Szat on 2011-02-05
Thanks for helping me out. I have checked the disk (USB) for errors and it didn't contain any. It still "thinks" at the preparing to install ubuntu screen after the language select. 
 
One thing I did find out was my hdd already had 4 partitions on it (came that way) and I was able to get a copy of SuperOS on it after deleting partitions. However, when I upgraded through the terminal from 9.x to 10.04 (didn't give me 10.10, don't know why)I started getting video errors that would freeze my system. I am using Nvidia's drivers.

I'm willing to format my hdd, because I didn't even want Windows on it to begin with.  I'm only worried that I will not be able to put an OS on my hdd because of all the trouble I'm having. I know that doesn't make sense, but it's a risk I might have to take.

---

### Post by Szat on 2011-02-05
Maybe I'm not creating the bootable usb drive correctly. After I check the hash I use Universal USB Installer and it creates the drive for me. My Computer in Windows does not show the Ubuntu icon of people holding hands for that drive and just shows a generic icon for a drive. When I mount the image with Daemon tools it shows that Ubuntu icon. Am I ready to use that drive to install now? Or is there another step? Do I need to use that USB-creator app in the USB drives files? Sorry about all the questions, but I've been working on this problem for a good 10 hours now.  Haven't been able to enjoy my new investment yet    :(

---

### Post by kansasnoob on 2011-02-06
Now that you're past the 4 primary problem this sounds very much like a compatibility problem with the Nvidia gpu. Since you have some Live USB running please post the output of:

```
lspci | grep VGA
```

That may provide more specifics about the Nvidia chip. There are some notes in both the 10.04 and 10.10 release notes:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display)

---

### Post by Szat on 2011-02-06
04:00.0 VGA compatible controller: nVidia Corporation Device 0a6f (rev a2)

---

