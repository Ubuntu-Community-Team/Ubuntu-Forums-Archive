---
title: "[SOLVED]Installation of ubuntu 16.04, update problems"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by arcanumwall on 2016-10-07
Morning everybody,

I just install ubuntu 16.04 from a USB key. I let the installation progress without internet connection. I want know to do the necessary upgrades and i started with a" sudo apt-get update"
The terminal send me this folllowing error message :


```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_xenial_universe_i18n_Translation-fr
E: Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus.
```

I also receive many error message and i can't open the update manager.
What can I do ?

---

### Post by RobGoss on 2016-10-07
Hello is this  a fresh installation of Ubuntu? 

Are you trying to dual boot your system?

Sometimes the source were you're downloading from may not be suitable trying changing it to see if you can run the updater. Open up **Software & updates** and from the source list choose a different server then just save and close out everything and try to update again

---

### Post by arcanumwall on 2016-10-07
I installed ubuntu this morning and no i'm not trying to dual boot. 

I switched into the principal server and i get this message : 

"important error ;
E:Problem parsing dependency Depends, E:Error occurred while processing fusiondirectory-plugin-freeradius-schema (NewVersion2), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened."

---

### Post by RobGoss on 2016-10-07
If this is a new installation I would suggest trying to reinstall Ubuntu again and see if that fixes what every issues your having at this point seeing this is a new installation

---

### Post by howefield on 2016-10-07
You could try

```
sudo rm -rf /var/lib/apt/lists
```

and then rebuild them with

```
sudo apt update
```

---

### Post by arcanumwall on 2016-10-07
With apt update i get after many downloads : 

```
Lecture des listes de paquets... Erreur !                      
E: Malformed Description-md5 line; includes invalid character '3e2a03&#65533;dd9fcc5d8036b9441e183901d'
E: Malformed Description-md5 line; includes invalid character '3e2a03&#65533;dd9fcc5d8036b9441e183901d'
E: Malformed Description-md5 line; includes invalid character '2ea6efQec3fbb8ba316b75ba53436f46'
E: Malformed Description-md5 line; includes invalid character '2ea6efQec3fbb8ba316b75ba53436f46'
E: Malformed Description-md5 line; includes invalid character 'd8c361e19ebae6a81&#65533;a8809f8df54db9'
E: Malformed Description-md5 line; includes invalid character 'd8c361e19ebae6a81&#65533;a8809f8df54db9'
W: Vous pouvez lancer « apt-get update » pour corriger ces problèmes.
E: Le fichier de cache des paquets est corrompu
```

---

### Post by howefield on 2016-10-07
Would you mind trying again with these three commands..

```
sudo rm -r /var/lib/apt/lists/*
```
```
sudo mkdir /var/lib/apt/lists/partial
```
```
sudo apt-get update
```

---

### Post by arcanumwall on 2016-10-07
I get at end : 

```
Lecture des listes de paquets... Erreur !
E: Problem parsing dependency Depends
E: Erreur apparue lors du traitement de ubuntu-keyboard-icelandic (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
E: Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus.


```

---

### Post by howefield on 2016-10-07
I'm struggling with the French I'm afraid, but try this if the status file is bad in some way.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get update
```

---

### Post by arcanumwall on 2016-10-07
In English for the precedent message : 

```
List package reading... Error !
E: Problem parsing dependency Depends
E: Erreur apparue lors du traitement de ubuntu-keyboard-icelandic (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
E: The package list or the data « status » cannot be analyzed or read.
```

With the new code line after  


```
sudo mv /var/lib/dpkg/status /var/lib/dpgk/status.bad
```

I obtain :

```
mv: impossible to move '/var/lib/dpkg/status' to '/var/lib/dpgk/status.bad': No file or folder of this type.
```

---

### Post by ubfan1 on 2016-10-07
Did you hashcheck the ISO you downloaded? See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.

---

### Post by howefield on 2016-10-08
OK, let's see if the status file really is missing, can you post..

```
ls -al /var/lib/dpkg/
```

if the status file is not there but the status-old file is, then do

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

then try to update.

---

### Post by arcanumwall on 2016-10-08
So , ls -al /var/lib/dpkg/ return me :

```
total 3908
drwxr-xr-x  7 root root    4096 oct.   7 12:41 .
drwxr-xr-x 65 root root    4096 oct.   7 12:44 ..
drwxr-xr-x  2 root root    4096 oct.   7 12:40 alternatives
-rw-r--r--  1 root root      11 oct.   7 12:36 arch
-rw-r--r--  1 root root  170080 juil. 19 22:42 available
-rw-r--r--  1 root root       8 juil. 19 22:42 cmethopt
-rw-r--r--  1 root root    1044 oct.   7 12:37 diversions
-rw-r--r--  1 root root    1079 oct.   7 12:37 diversions-old
drwxr-xr-x  2 root root  352256 oct.   7 12:40 info
-rw-r-----  1 root root       0 oct.   7 12:41 lock
drwxr-xr-x  2 root root    4096 janv. 12  2016 parts
-rw-r--r--  1 root root     228 juil. 19 22:49 statoverride
-rw-r--r--  1 root root 1716212 oct.   7 12:41 status
-rw-r--r--  1 root root 1716212 oct.   7 12:41 status-old
drwxr-xr-x  2 root root    4096 oct.   7 12:40 triggers
drwxr-xr-x  2 root root    4096 oct.   7 12:41 updates


```

so, status and status-old are here ... shall i do  
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```
?

---

### Post by howefield on 2016-10-08
> **arcanumwall said:**
> so, status and status-old are here ... shall i do  
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```

That would wipe out the existing status file with no backup copy, I'd be reluctant to do that.

I'd try again with the commands, I'm just noticing that you made a typo which caused the command to fail.. you used

```
sudo mv /var/lib/dpkg/status /var/lib/dpgk/status.bad
```

note the "dpgk" in the destination, it should be "dpkg"

Try again,
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get update
```

---

### Post by arcanumwall on 2016-10-08
Oh yes indeed .. my bad ^^'
so it return me 

```
Package list reading... Error !
E: Problem parsing dependency Depends
E: Error occurred while processing ubuntu-keyboard-icelandic (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
E: The packages lists or the file « status » cannot be analyzed or read.


```


Ubfan1 , I don't know beacause i don't have the original iso anymore. But on the USB key used to mount it I have a file md5sum.txt. The problem is that I really don't know where I can found the information in.

```
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
24ec176894c781355f9ccb08ba69919e  ./preseed/ubuntu.seed
0391854d1af5a015a667f29fa0442e78  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
389fcba22756fd0ee4d4d41c68911793  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb
e8a45c9674b27a8c5adf303fe31d723d  ./pool/restricted/i/intel-microcode/intel-microcode_3.20151106.1_amd64.deb
6a1a9a29d1b9f999d99f072eb243f111  ./pool/restricted/i/iucode-tool/iucode-tool_1.5.1-1_amd64.deb
051d08864162eb511ce90b9609481af5  ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu9_amd64.deb
64c73e8a60c3a3d5fdc9c384a614188f  ./pool/main/l/lupin/lupin-support_0.57_amd64.deb
9ef3862968ebeb9e86ff856406800bd2  ./pool/main/s/shim-signed/shim-signed_1.17~16.04.1+0.8-0ubuntu2_amd64.deb
1915dc237a738b6f5c1f3adfe997809d  ./pool/main/s/shim/shim_0.8-0ubuntu2_amd64.deb
b900209ffcda1906ca8b75dea87a2b76  ./pool/main/s/setserial/setserial_2.17-49_amd64.deb
b3a2dcbcb59ba1a7245b409649cb84dc  ./pool/main/g/grub2/grub-efi-amd64-bin_2.02~beta2-36ubuntu3.1_amd64.deb
c67f7b5bb1a4b7c7c08e90859adfd3fd  ./pool/main/g/grub2/grub-efi-amd64_2.02~beta2-36ubuntu3.1_amd64.deb
911721a4bdf493c7036d55f477dbf22a  ./pool/main/g/grub2/grub-efi_2.02~beta2-36ubuntu3.1_amd64.deb
964d185d67b19b2a5597029bcb8b8804  ./pool/main/g/glibc/libc6-i386_2.23-0ubuntu3_amd64.deb
81dc3235954662388e099e56bebf087c  ./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.66.1+2.02~beta2-36ubuntu3.1_amd64.deb
8d81686b97d257c8936cf7cd5150289b  ./pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb
7f41742fe3a4e6b62b24a832ac401e87  ./pool/main/b/b43-fwcutter/b43-fwcutter_019-2_amd64.deb
fee6246e273ba9c2ff39385918e3f52a  ./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-7_amd64.deb
10638bcd250ccf702637a64d6c1f21d4  ./pool/main/w/wvstreams/libuniconf4.6_4.6.1-7_amd64.deb
275d85005fe762aa48e8a8103fd5a22d  ./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-7_amd64.deb
b878702b4959ae848ed7568523f35eee  ./pool/main/w/wvdial/wvdial_1.61-4.1_amd64.deb
cc0c08b5fe6b5d16802eb31a249f17a5  ./pool/main/u/user-setup/user-setup_1.63ubuntu4_all.deb
04e4fe6c7f92a653c7339c22a358ae13  ./pool/main/u/ubiquity/oem-config-gtk_2.21.63.2_all.deb
774749371f15f44a18216859df0ddcac  ./pool/main/u/ubiquity/oem-config_2.21.63.2_all.deb
a80f49c70f6f12d2a9ad4324f19b51bb  ./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_113_all.deb
d16da7ca2021458ace5caf391d9c2f38  ./pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11.1_all.deb
86e52e9dae2422a43a88fdd955990a1e  ./.disk/info
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
8ad1af67bf1afe989aeb986b7aef6f9f  ./.disk/casper-uuid-generic
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
f5ba71c0bf2432b4e0efee640a388a18  ./.disk/release_notes_url
ded965934506efb38a6dcb9ac5b2b79e  ./EFI/BOOT/BOOTx64.EFI
99f8063cee7130fe2489ee39f13cde4c  ./EFI/BOOT/grubx64.efi
7d50afa359128e6ced6dae1ff24f4f9c  ./boot/grub/x86_64-efi/chain.mod
40d9574e2fed819dd2ae90f0b99ada71  ./boot/grub/x86_64-efi/blocklist.mod
deea49dca4bb4d8ee32410df3742e853  ./boot/grub/x86_64-efi/spkmodem.mod
a07414ab3f1d106cb7d4541f7e6a8aca  ./boot/grub/x86_64-efi/loopback.mod
220468c697c2d1a88a3652ad71579386  ./boot/grub/x86_64-efi/pata.mod
624144e4bba3f3b91f68093e22bf70b3  ./boot/grub/x86_64-efi/echo.mod
10bfbec68887d92afe5b8e7e6052da7f  ./boot/grub/x86_64-efi/lsacpi.mod
0dc6774d7d31a0f465c7bfc4dd4e2f0d  ./boot/grub/x86_64-efi/gcry_sha256.mod
36d4eb5ea47637ed558666211808b80c  ./boot/grub/x86_64-efi/cbls.mod
8ceeab66eee348152f3035dcaddf7f5c  ./boot/grub/x86_64-efi/part_acorn.mod
4a4948d58e0232e27ee7034ce57f9520  ./boot/grub/x86_64-efi/videotest.mod
7ed566e96a42a637026bde2a42a37b55  ./boot/grub/x86_64-efi/gettext.mod
cbbdc0b9279ce4e4308b9e54e157a444  ./boot/grub/x86_64-efi/iorw.mod
9591a831e8aaff1f9281c49b007b29dd  ./boot/grub/x86_64-efi/acpi.mod
f82413f156ff4c93f796eab5f70830e3  ./boot/grub/x86_64-efi/part_sun.mod
1420a78feca223a4f7388d00c0a7e53d  ./boot/grub/x86_64-efi/terminfo.mod
d60e3ff04157ca0eb968611e01019821  ./boot/grub/x86_64-efi/minix3_be.mod
7f2d6352c2d2c2619f1f52ccab92e8d3  ./boot/grub/x86_64-efi/ohci.mod
df73a02dd4d49a4d1dcd8dc7fce649bb  ./boot/grub/x86_64-efi/gcry_arcfour.mod
fde9e8d2ffe6a27052f1b4636611dbef  ./boot/grub/x86_64-efi/raid6rec.mod
db307636342475acb0f5bd056d0bc17e  ./boot/grub/x86_64-efi/gfxmenu.mod
901cbc618b55df532f1631bedbf4c5b8  ./boot/grub/x86_64-efi/xnu_uuid_test.mod
e860763cb8c1bca0201b9295c4cebe95  ./boot/grub/x86_64-efi/morse.mod
38a64f99650768851225b2ae0a2f9be2  ./boot/grub/x86_64-efi/efi_uga.mod
fd3d238090b5bdf5df6b4f6c2aafa18b  ./boot/grub/x86_64-efi/part_apple.mod
45a1d9cb7081cdac900acf8442fd3705  ./boot/grub/x86_64-efi/video_bochs.mod
9449e44c53a9e5ac4b179a4b2a7d7a2c  ./boot/grub/x86_64-efi/dm_nv.mod
8f9eb214d127d8d31d6bf8809a93052f  ./boot/grub/x86_64-efi/gcry_camellia.mod
10b48eda1acbb623fbd60f2cbcb9d348  ./boot/grub/x86_64-efi/multiboot2.mod
9a273c817389c962823927ad7cba3658  ./boot/grub/x86_64-efi/bitmap.mod
0dbb794afe012a265a82a4aefcd231e4  ./boot/grub/x86_64-efi/part_plan.mod
4f8b9e79717d7a04f1801a147599e1be  ./boot/grub/x86_64-efi/usb_keyboard.mod
446bb4f84307fdaee96c617e39f2fe12  ./boot/grub/x86_64-efi/efifwsetup.mod
4d382c883544665ac3570bc1ea76cdde  ./boot/grub/x86_64-efi/part_amiga.mod
3190a91d3075032543740d0998971d77  ./boot/grub/x86_64-efi/parttool.lst
d3bdff701214d3dcba7586d6321613b8  ./boot/grub/x86_64-efi/boot.mod
70e8242c6c0bbc917dea252aa5654279  ./boot/grub/x86_64-efi/hfs.mod
9483ef6ea033fd2b0f4d9258c7b15e19  ./boot/grub/x86_64-efi/eval.mod
02b988d7196362ddf27caaecf35c23dc  ./boot/grub/x86_64-efi/partmap.lst
477ce336e0c66ba15af4c38ade5f7945  ./boot/grub/x86_64-efi/adler32.mod
55f0c3325ce41fd4e8bee7cb66a9ddbf  ./boot/grub/x86_64-efi/btrfs.mod
7d9829cb149255a75e7f143c74fc99d9  ./boot/grub/x86_64-efi/gcry_serpent.mod
a981bdcf91fb3ff2d3e59643a50d1a2b  ./boot/grub/x86_64-efi/setjmp_test.mod
36fb2915eff0494e8dc76adf023435fa  ./boot/grub/x86_64-efi/cpio_be.mod
a3db63c9fc6da35a00048449c1518f67  ./boot/grub/x86_64-efi/tftp.mod
99caf41bcb348cbccad9f49fce6f9296  ./boot/grub/x86_64-efi/lsefi.mod
0bedbb665427878ad6c512bfe30b4dfb  ./boot/grub/x86_64-efi/xnu_uuid.mod
d9c6f2d1d0706823dbb1fddd9c754e54  ./boot/grub/x86_64-efi/test.mod
21ca35be46eea3a4331d1ad61d85d725  ./boot/grub/x86_64-efi/syslinuxcfg.mod
117f3676a8ac31b9962e2d3c7886e6bf  ./boot/grub/x86_64-efi/test_blockarg.mod
7e2e5e5392bb4c113230e002c7675b53  ./boot/grub/x86_64-efi/part_msdos.mod
35d511932ce2930f3e048989f1fefb5a  ./boot/grub/x86_64-efi/datetime.mod
1a3970f914794b3e45ffec2e1303c600  ./boot/grub/x86_64-efi/keystatus.mod
3c70c511691ecea3e2e8b809eaa56097  ./boot/grub/x86_64-efi/password.mod
2810dc2d532b0e1ed2e62c4f9daf1168  ./boot/grub/x86_64-efi/lsefimmap.mod
623d566621df9e55b2b100869b075276  ./boot/grub/x86_64-efi/halt.mod
bbde7707309e3ea76f9912931b1c4ffa  ./boot/grub/x86_64-efi/luks.mod
7d86acc3d68833f22603dc5859e8ebdc  ./boot/grub/x86_64-efi/video.lst
9390296c74d0be52de0b0e38938f2776  ./boot/grub/x86_64-efi/macbless.mod
d08c430c455b976035b06436e6b87004  ./boot/grub/x86_64-efi/geli.mod
bf757a132294638852e825ed3fda201b  ./boot/grub/x86_64-efi/gcry_tiger.mod
345b8a775232f6b759df571eee2a0245  ./boot/grub/x86_64-efi/gcry_rmd160.mod
1255136ede7a0906467dd0df2e2ac441  ./boot/grub/x86_64-efi/part_sunpc.mod
4b0b99c64f7b17c68bebc11669f79477  ./boot/grub/x86_64-efi/raid5rec.mod
8ba8b5f7e7a10e333c2901fe3fb00bae  ./boot/grub/x86_64-efi/lspci.mod
098832497928edecd396096490b430de  ./boot/grub/x86_64-efi/terminal.lst
6a3f58db454b17a0a339323b3e134a6b  ./boot/grub/x86_64-efi/crypto.lst
16c5e889be08ff3fc3bf370d93ecd152  ./boot/grub/x86_64-efi/jpeg.mod
90e05cd2b2953176dba4254be6f9f7d2  ./boot/grub/x86_64-efi/video_fb.mod
6d2a8ae189dd0184f95acb1c51e37d5e  ./boot/grub/x86_64-efi/datehook.mod
2eb8a6bf2b72ab397541f7902bfcd516  ./boot/grub/x86_64-efi/cbtable.mod
21d6315e1be26b09ee85bc09aa3dc153  ./boot/grub/x86_64-efi/mpi.mod
41e6e89b1d12f263eb24180343bb3d1f  ./boot/grub/x86_64-efi/gcry_rijndael.mod
aa45c4cff449b23fe7c50ad5a07b492b  ./boot/grub/x86_64-efi/videoinfo.mod
1917fefc3c30851456d3439351746fb4  ./boot/grub/x86_64-efi/file.mod
e296f1a08656e5535c052a7873728602  ./boot/grub/x86_64-efi/testload.mod
3f44094d10d3a13ae922523125ad8eb0  ./boot/grub/x86_64-efi/gcry_twofish.mod
6c2da69df26c93aec6577faccced9421  ./boot/grub/x86_64-efi/lsefisystab.mod
e54e01ceb86ffd639f3ee1fec6aa9427  ./boot/grub/x86_64-efi/usbserial_usbdebug.mod
7b6dbb952c3963b2527aa2b6dffe754c  ./boot/grub/x86_64-efi/xfs.mod
a371a6e3d816dc824e5ce58f98338129  ./boot/grub/x86_64-efi/minix3.mod
98d785c0519c6701610ca858625dd5ab  ./boot/grub/x86_64-efi/ntfscomp.mod
cfc30d0d3d56ecae46b7784c514ab58f  ./boot/grub/x86_64-efi/minix2.mod
e2bdc849c500fb6248891539a96f999e  ./boot/grub/x86_64-efi/uhci.mod
7dc53b6e1cac450c2121f90b1a94f69b  ./boot/grub/x86_64-efi/testspeed.mod
b786495d7543bb5dce647a4554d22c92  ./boot/grub/x86_64-efi/jfs.mod
a2ff6f4de6f798f713147ea876717d59  ./boot/grub/x86_64-efi/help.mod
2059470498bc25c70bb4b30952856583  ./boot/grub/x86_64-efi/offsetio.mod
87e5f91fc0d41c627cd8b0cdc25e8415  ./boot/grub/x86_64-efi/videotest_checksum.mod
de13ddb3b486dedad5eb418b58320b7a  ./boot/grub/x86_64-efi/video_colors.mod
5a3bedce1860ec1769cb8ff16d1de91c  ./boot/grub/x86_64-efi/usb.mod
86adfc638a3a7e7b45030729ab3d6354  ./boot/grub/x86_64-efi/zfscrypt.mod
353f95d07ad3a6fd7e7085c36822ab94  ./boot/grub/x86_64-efi/setpci.mod
27b5e065ed82e43acc1e5a3ba54e7194  ./boot/grub/x86_64-efi/diskfilter.mod
4259446a742af1f7beeda97bc3e8f8cf  ./boot/grub/x86_64-efi/cat.mod
121d0d385251ebe4a39f598f9f6ad6f5  ./boot/grub/x86_64-efi/minicmd.mod
1e22adeef168684f7c5736313f3bfeb5  ./boot/grub/x86_64-efi/msdospart.mod
269954bf0dc449cf6b22d9e50a45e115  ./boot/grub/x86_64-efi/part_bsd.mod
bcbcd2704b5382e373c62de3ce8b0c4e  ./boot/grub/x86_64-efi/gcry_rsa.mod
25e2387edbe3af480b29883f9e2c4c8a  ./boot/grub/x86_64-efi/exfctest.mod
6b0616d1de6fc81c4b3f00105ca1e407  ./boot/grub/x86_64-efi/lvm.mod
3c9a99c6339c8762082100cbde6b6cf5  ./boot/grub/x86_64-efi/progress.mod
507cb3a0fb2a7c4a5688c29533094816  ./boot/grub/x86_64-efi/gcry_sha512.mod
337de99792ff47e2ecf67798aa8d4f4b  ./boot/grub/x86_64-efi/romfs.mod
8f9e79cd1c4b279109a6b1f91f53a4de  ./boot/grub/x86_64-efi/gfxterm_menu.mod
9a06749b7b222a22a1d24040873f3658  ./boot/grub/x86_64-efi/ufs1_be.mod
320633cea7b3f6922b5ffaa6063f659e  ./boot/grub/x86_64-efi/newc.mod
e44844992f62e31216b9fbb05b86a51a  ./boot/grub/x86_64-efi/true.mod
20a42b443e54be16def028a60a558982  ./boot/grub/x86_64-efi/aout.mod
7ce000563fd1e5247295f8c19e7fcaf4  ./boot/grub/x86_64-efi/gfxterm_background.mod
63057a2541a068da73e28a5bec8d7dc6  ./boot/grub/x86_64-efi/gcry_md4.mod
9800dc138162f0fe6b5c201a4fa18380  ./boot/grub/x86_64-efi/verify.mod
1347d8d36f4b759133251f6c2bc017f0  ./boot/grub/x86_64-efi/ehci.mod
65655023454b7325c57aaf0b8516ee04  ./boot/grub/x86_64-efi/video.mod
6d6fb3d6e21f37cdea26009aa5e51f86  ./boot/grub/x86_64-efi/http.mod
25489bad8f7f2c0e6a1dd07c01ea4998  ./boot/grub/x86_64-efi/gcry_des.mod
2dd02959f3531e87eb3d03e11e161133  ./boot/grub/x86_64-efi/cryptodisk.mod
122e08b130cfed2966ea0c3d40354e8b  ./boot/grub/x86_64-efi/usbserial_common.mod
1000f16a0842be20b22262eedc3059cb  ./boot/grub/x86_64-efi/backtrace.mod
dafd5a250c3fc0eb4fb2e5aaeb08da5c  ./boot/grub/x86_64-efi/fat.mod
4f538fe39728a1867930c7a138d083e4  ./boot/grub/x86_64-efi/xnu.mod
b8f525a3d773a690fc4519226d29ec26  ./boot/grub/x86_64-efi/lssal.mod
5917237447c3c9f99cf901e9e2d4be32  ./boot/grub/x86_64-efi/efinet.mod
04aca706c146767c521c76009cd3afac  ./boot/grub/x86_64-efi/div_test.mod
a105ed65e2f91069ba7d7f6dadf00ee5  ./boot/grub/x86_64-efi/grub.cfg
5a22db3b4c580d117352b0fd5941e8c6  ./boot/grub/x86_64-efi/crc64.mod
e20df939c6b906c10ee5fda227c91bb5  ./boot/grub/x86_64-efi/pcidump.mod
39d7eeb2477d38b32a823a308d2cf730  ./boot/grub/x86_64-efi/date.mod
3a4ee7c0d4f01589618c0b5c0d7800ae  ./boot/grub/x86_64-efi/parttool.mod
5dcad7c40a69ecb5dd005ef66be5035f  ./boot/grub/x86_64-efi/ldm.mod
34b4df6c844dcf605f5400cb07a343b3  ./boot/grub/x86_64-efi/gcry_sha1.mod
e8e89b08e9027298a582b011bbb83a32  ./boot/grub/x86_64-efi/memrw.mod
eb9da5626463574ee971569bb11434af  ./boot/grub/x86_64-efi/gcry_crc.mod
991fce53753c5c178325aba30b77ce2e  ./boot/grub/x86_64-efi/png.mod
133e02809276439049e281739e7c40f4  ./boot/grub/x86_64-efi/hfspluscomp.mod
c41a81d8bfe8e08557132642bb7cdb00  ./boot/grub/x86_64-efi/hexdump.mod
97c5f176e1b47f4afeb73f1efb0f693e  ./boot/grub/x86_64-efi/ntfs.mod
b768aa2d77fae7798fa957f75220fb3a  ./boot/grub/x86_64-efi/keylayouts.mod
ea72253497e2335d0bf1d66b43e384c9  ./boot/grub/x86_64-efi/gcry_md5.mod
94496d4cf1970d229e3d306f780e5f55  ./boot/grub/x86_64-efi/gcry_dsa.mod
11da1e38f280cc85b6a9957d0a904864  ./boot/grub/x86_64-efi/bfs.mod
0d39a66f2f789414473fec53a672cef9  ./boot/grub/x86_64-efi/usbserial_ftdi.mod
266a8a94ca53fc866d582582b8574bbf  ./boot/grub/x86_64-efi/sleep_test.mod
38735499694acc6ad351d074478dd506  ./boot/grub/x86_64-efi/efi_gop.mod
ece14d534ac7e9b25f9425ff9ab850d3  ./boot/grub/x86_64-efi/gcry_whirlpool.mod
a76dfa69eca75d1a7570f18e36b0c10e  ./boot/grub/x86_64-efi/lzopio.mod
c3c47102f7ea5edb84cf858c7304ec84  ./boot/grub/x86_64-efi/at_keyboard.mod
0fa4bc93383668355152b776d7267c7a  ./boot/grub/x86_64-efi/gptsync.mod
67bdfdaeac1525961482a205f1900bd8  ./boot/grub/x86_64-efi/minix2_be.mod
8be4c0a46752a2ce80d6f30720ca664b  ./boot/grub/x86_64-efi/relocator.mod
3df3170b321417cfdd0d29c518097c1d  ./boot/grub/x86_64-efi/hashsum.mod
026b99b910da3b0a73200b064d9690c7  ./boot/grub/x86_64-efi/usbserial_pl2303.mod
1ef10edc000cd184d54a49efe25a6b1e  ./boot/grub/x86_64-efi/mdraid09.mod
0309998eeb157af28fb0b5bdbaf5bf13  ./boot/grub/x86_64-efi/ata.mod
ecba620519d37b776f6d6acae4268de2  ./boot/grub/x86_64-efi/ufs1.mod
8eac644daeba9e54748fb0f173334a75  ./boot/grub/x86_64-efi/procfs.mod
b8e13afb76e19750d7a74bbdebc81289  ./boot/grub/x86_64-efi/elf.mod
47936d1add17c963e14bedbf73e63a89  ./boot/grub/x86_64-efi/gfxterm.mod
c94f5a2289f77e38666db35422068187  ./boot/grub/x86_64-efi/cpio.mod
899077309944b3af4fa6d6fc4cc959f4  ./boot/grub/x86_64-efi/ls.mod
90342a0796614bc575dc2dafefa320f7  ./boot/grub/x86_64-efi/mmap.mod
41363fc28cade481ba6f4b16f2ba049b  ./boot/grub/x86_64-efi/odc.mod
75a892b712c4448b7406ebd8af7d5c48  ./boot/grub/x86_64-efi/hfsplus.mod
b2467d9a58f00b49456f55b89d17d242  ./boot/grub/x86_64-efi/crypto.mod
8ddcd9e879e38c45430a814936ff109e  ./boot/grub/x86_64-efi/gcry_idea.mod
4a601270e2425840c7582c7d936a3520  ./boot/grub/x86_64-efi/net.mod
431c22417af9462274be0d2ded40de9f  ./boot/grub/x86_64-efi/gcry_rfc2268.mod
ce79c4cb56266f6af53e00a68aca8978  ./boot/grub/x86_64-efi/legacycfg.mod
ce8860680d0dcff183ca10958813ca1f  ./boot/grub/x86_64-efi/pbkdf2_test.mod
79f7d749a2035c8010939224ca2f42a8  ./boot/grub/x86_64-efi/cpuid.mod
54055f3cff32a29c3585e89022ad31e6  ./boot/grub/x86_64-efi/bsd.mod
93e0b8f01c3ad964d013850262623ffe  ./boot/grub/x86_64-efi/part_dvh.mod
707f3970abbd7f5c4b56bd44670a21d6  ./boot/grub/x86_64-efi/sleep.mod
f19ba1e7df5bad8cfb41f88eb60407c6  ./boot/grub/x86_64-efi/fixvideo.mod
1a599beac5adca1d2e769343949176bb  ./boot/grub/x86_64-efi/setjmp.mod
87e82d5a545414ad71c1b7f8e2c5db8a  ./boot/grub/x86_64-efi/read.mod
c5ff564a501c55d8bddaf26aee9d586f  ./boot/grub/x86_64-efi/macho.mod
a51f2eaffcd2e0888be4e822c6f7cb9c  ./boot/grub/x86_64-efi/gcry_blowfish.mod
84f929a7bd0b2acb82a0d3557c9380bf  ./boot/grub/x86_64-efi/squash4.mod
777e2a7ba3839e73a7c3c3c5d43c4bcf  ./boot/grub/x86_64-efi/multiboot.mod
05dc5b7eb81216e010d10b171dd8a434  ./boot/grub/x86_64-efi/password_pbkdf2.mod
bf590e006a0f692c42f22d3803cb2bc2  ./boot/grub/x86_64-efi/ext2.mod
549aa7cda3849f6bf3f6808249095a1a  ./boot/grub/x86_64-efi/bitmap_scale.mod
9ca1f80ff7d4dd06bdce7c926620137d  ./boot/grub/x86_64-efi/archelp.mod
9aafcdfd75a849a6c57c519fac8116d1  ./boot/grub/x86_64-efi/moddep.lst
7bb4810fd4cf3540dd719670923b4282  ./boot/grub/x86_64-efi/mdraid1x.mod
a43dc3c9677e1aaba478590b4a2e95c7  ./boot/grub/x86_64-efi/reiserfs.mod
3bc08fd9d39679236ef156ec528f146e  ./boot/grub/x86_64-efi/cmp.mod
eeeda090212fe67f0e81c738a425bc93  ./boot/grub/x86_64-efi/fs.lst
e90225392f29ca0aa57984eded1e34f7  ./boot/grub/x86_64-efi/loadbios.mod
b8b4857cbec24e9f3f25795e09dcb079  ./boot/grub/x86_64-efi/linuxefi.mod
6b57f80bc8897f1073c54af4aa5c5afb  ./boot/grub/x86_64-efi/hdparm.mod
981c85d4056c05e6b9371c62cf4a3935  ./boot/grub/x86_64-efi/signature_test.mod
e9fa4386ab8da7519e0f52fb30037e6f  ./boot/grub/x86_64-efi/cbtime.mod
815b1fe6f544e464cbe32cbf2eca4432  ./boot/grub/x86_64-efi/cbmemc.mod
d560df0418ccb0f6dcd5d27ba6331bec  ./boot/grub/x86_64-efi/command.lst
d08b71ba7d94aedadcecad5a549a1005  ./boot/grub/x86_64-efi/scsi.mod
d2d939b4f16d5a62596967f3557e3119  ./boot/grub/x86_64-efi/tr.mod
2e1f3a3dba234cdeef6223a518b9f740  ./boot/grub/x86_64-efi/play.mod
3742eba3d74efe9a2dc4e3fab171be06  ./boot/grub/x86_64-efi/ufs2.mod
b6e7f332c562657baa90c92cef062d85  ./boot/grub/x86_64-efi/mdraid09_be.mod
42020339f873a870d196ec072affca39  ./boot/grub/x86_64-efi/loadenv.mod
58d81b5675e2d5071c7582ac84dd46f3  ./boot/grub/x86_64-efi/all_video.mod
2a1adead8b9c1640dbd7dbb98b1b8147  ./boot/grub/x86_64-efi/linux16.mod
d6a64444a38cf68d857c37c4a54602cb  ./boot/grub/x86_64-efi/xzio.mod
40f1337423669f0af9f02946c08edf68  ./boot/grub/x86_64-efi/font.mod
b2c31dd58f8ee1932d7655d2c3e1e99c  ./boot/grub/x86_64-efi/ahci.mod
65ec05839d2e4abb1da4c17356dcc62c  ./boot/grub/x86_64-efi/time.mod
c244c0c3b36a236dd8c2877293b2a5e9  ./boot/grub/x86_64-efi/part_dfly.mod
3620aad98117fb90c253fecdd1e2f58b  ./boot/grub/x86_64-efi/appleldr.mod
1caa4060faad961195371641ef70d35b  ./boot/grub/x86_64-efi/cs5536.mod
8e2313debaef370b69a944f87c4a461a  ./boot/grub/x86_64-efi/linux.mod
c762d5dcb76a88ef5ae2c1a1b29f0244  ./boot/grub/x86_64-efi/gcry_cast5.mod
e3d4bc29a265f8fb04114cf4d6eaefd7  ./boot/grub/x86_64-efi/reboot.mod
87b4b8ba57c0f704ab06d7523d261b8b  ./boot/grub/x86_64-efi/lsmmap.mod
dccc00151e4295e350029683bb3fbaf7  ./boot/grub/x86_64-efi/gzio.mod
a8345fe08e03481efea23767c4c46c2f  ./boot/grub/x86_64-efi/usbtest.mod
f18b30691200956f8bb597359d884259  ./boot/grub/x86_64-efi/legacy_password_test.mod
a716aaf63a0ccb8cb19d2d4e39b755f5  ./boot/grub/x86_64-efi/bufio.mod
1ba9f003e4f4709a791daad5a51f1bc3  ./boot/grub/x86_64-efi/udf.mod
befcca593c61748d84a2591b5d651253  ./boot/grub/x86_64-efi/pbkdf2.mod
d5f6eb3c9e6d61279b12dd88a934e006  ./boot/grub/x86_64-efi/video_cirrus.mod
bd642af7a81cf7bfea6c89d9d2b089ad  ./boot/grub/x86_64-efi/nativedisk.mod
0cd5531d9c94648e2476533551ab5c22  ./boot/grub/x86_64-efi/disk.mod
a102352bba4f24ea948405a5e74e9d40  ./boot/grub/x86_64-efi/cbfs.mod
bacaa18d0e40bc5f7ca2081d2e34d284  ./boot/grub/x86_64-efi/cmdline_cat_test.mod
29569bd656ed39820e5136dee596a01c  ./boot/grub/x86_64-efi/regexp.mod
5575048d1581073c5ce14a8bdb877e8a  ./boot/grub/x86_64-efi/minix_be.mod
7d770542891ca8bb84ae36d7873cd9f6  ./boot/grub/x86_64-efi/priority_queue.mod
1ffcd0af07d0799dadd38e21bb33fe0c  ./boot/grub/x86_64-efi/trig.mod
6283e87e9f1a4740e3471a050f099350  ./boot/grub/x86_64-efi/tga.mod
528f5520c1d326f0d206465cea49d4a2  ./boot/grub/x86_64-efi/usbms.mod
7be5e72ceed1f9936415d0631d620155  ./boot/grub/x86_64-efi/terminal.mod
c88c0c123db9b76c72f6969f5fff3631  ./boot/grub/x86_64-efi/gcry_seed.mod
8ced7d0800c4d5697eda014cb340004b  ./boot/grub/x86_64-efi/exfat.mod
dc0e5bffcc10a43ef59ebe4e68a60ecf  ./boot/grub/x86_64-efi/serial.mod
69a1ea271fdf817d35f85c790b847811  ./boot/grub/x86_64-efi/probe.mod
cea715379bc91984ca3b3a54afbb67be  ./boot/grub/x86_64-efi/part_gpt.mod
a943fee9aca1691e7af52f732cdc9909  ./boot/grub/efi.img
c915bde902be381c9c268c01fb506e0e  ./boot/grub/grub.cfg
0bf15b6e65732c8efb9793eba1e228b0  ./boot/grub/loopback.cfg
a52811f3a41e15b01c4cc2551294e8c8  ./boot/grub/font.pf2
2e931bf0a8eb2451e582c8aef9d0d231  ./casper/filesystem.size
65941ba3435fcfe8f123e43430489509  ./casper/filesystem.manifest
ce852f59df20cb04da5c377f8d79530d  ./casper/filesystem.squashfs
3892abefbe1e079c92dded198848d0e0  ./casper/filesystem.squashfs.gpg
3e39ef46c428bf4b74e0cbe516f47823  ./casper/initrd.lz
e8dc1e67271d4074f52224d2fe6f10c6  ./casper/vmlinuz.efi
dd0ea9cd35b4e5e9f804955e6da35b28  ./casper/filesystem.manifest-remove
8415340be36a7573655f63cb43a1a7c7  ./README.diskdefines
be5a6215c8365ad6fcccfb5e5febdfa3  ./dists/xenial/restricted/binary-i386/Release
4a4dd3598707603b3f76a2378a4504aa  ./dists/xenial/restricted/binary-i386/Packages.gz
ea93f2e671df19668c74e9b01defa440  ./dists/xenial/restricted/binary-amd64/Release
dbec8e438af28b84accdd29ff654c322  ./dists/xenial/restricted/binary-amd64/Packages.gz
5011a93d20f3e47b7c86f8e44f07d886  ./dists/xenial/Release
1c5f450104c475e7ef28e353020b083f  ./dists/xenial/Release.gpg
4b055b3443971f13d049b8f474ad3af2  ./dists/xenial/main/binary-i386/Release
4a4dd3598707603b3f76a2378a4504aa  ./dists/xenial/main/binary-i386/Packages.gz
3da37ac4e874215ba57d3024828e50b4  ./dists/xenial/main/binary-amd64/Release
300266a23cb1d337c74f2a216e924429  ./dists/xenial/main/binary-amd64/Packages.gz
f0fc0ff4ad6055c3a6ba5524de414fcd  ./install/mt86plus
```

---

### Post by howefield on 2016-10-08
> **arcanumwall said:**
> Ubfan1 , I don't know beacause i don't have the original iso anymore. But on the USB key used to mount it I have a file md5sum.txt. The problem is that I really don't know where I can found the information in.

You can navigate to the USB stick in a terminal and use

```
md5sum -c md5sum.txt
```

which will check each file on the USB against the md5sum.txt file you mention above. It will probably take a few minutes to complete so don't worry if it appears to stall. 

Eg.
```
hugh@yakkety-laptop:/media/hugh/Ubuntu 16.10 amd64$ md5sum -c md5sum.txt
./pics/red-upperleft.png: OK
./pics/red-lowerleft.png: OK
./pics/blue-lowerleft.png: OK
./pics/logo-50.jpg: OK
./pics/blue-upperright.png: OK
./pics/blue-lowerright.png: OK
./pics/red-lowerright.png: OK
./pics/blue-upperleft.png: OK
./pics/debian.jpg: OK
./pics/red-upperright.png: OK
./preseed/ubuntu.seed: OK
./preseed/ltsp.seed: OK
./preseed/cli.seed: OK
./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu11_amd64.deb: OK
./pool/restricted/i/intel-microcode/intel-microcode_3.20160714.1_amd64.deb: OK
./pool/restricted/i/iucode-tool/iucode-tool_1.6.1-1_amd64.deb: OK
./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu9_amd64.deb: OK
./pool/main/l/lupin/lupin-support_0.57_amd64.deb: OK
./pool/main/s/shim-signed/shim-signed_1.21.2+0.9+1465500757.14a5905.is.0.8-0ubuntu2_amd64.deb: OK
./pool/main/s/shim/shim_0.9+1465500757.14a5905.is.0.8-0ubuntu2_amd64.deb: OK
./pool/main/s/setserial/setserial_2.17-49.1_amd64.deb: OK
./pool/main/g/grub2/grub-efi-amd64_2.02~beta2-36ubuntu11_amd64.deb: OK
./pool/main/g/grub2/grub-efi-amd64-bin_2.02~beta2-36ubuntu11_amd64.deb: OK
./pool/main/g/grub2/grub-efi_2.02~beta2-36ubuntu11_amd64.deb: OK
./pool/main/g/glibc/libc6-i386_2.24-0ubuntu1_amd64.deb: OK
./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.74+2.02~beta2-36ubuntu11_amd64.deb: OK
./pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb: OK
./pool/main/b/b43-fwcutter/b43-fwcutter_019-3_amd64.deb: OK
./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-10_amd64.deb: OK
./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-10_amd64.deb: OK
./pool/main/w/wvstreams/libuniconf4.6_4.6.1-10_amd64.deb: OK
./pool/main/w/wvdial/wvdial_1.61-4.1_amd64.deb: OK
./pool/main/u/user-setup/user-setup_1.63ubuntu4_all.deb: OK
./pool/main/u/ubiquity/oem-config_16.10.11_all.deb: OK
./pool/main/u/ubiquity/oem-config-gtk_16.10.11_all.deb: OK
./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_116_all.deb: OK
./pool/main/d/dkms/dkms_2.2.0.3-2ubuntu14_all.deb: OK
./.disk/info: OK
./.disk/base_installable: OK
./.disk/casper-uuid-generic: OK
./.disk/cd_type: OK
./.disk/release_notes_url: OK
./EFI/BOOT/BOOTx64.EFI: OK
./EFI/BOOT/grubx64.efi: OK
./boot/grub/x86_64-efi/chain.mod: OK
./boot/grub/x86_64-efi/blocklist.mod: OK
./boot/grub/x86_64-efi/spkmodem.mod: OK
./boot/grub/x86_64-efi/loopback.mod: OK
./boot/grub/x86_64-efi/pata.mod: OK
./boot/grub/x86_64-efi/echo.mod: OK
./boot/grub/x86_64-efi/lsacpi.mod: OK
./boot/grub/x86_64-efi/gcry_sha256.mod: OK
./boot/grub/x86_64-efi/cbls.mod: OK
./boot/grub/x86_64-efi/part_acorn.mod: OK
./boot/grub/x86_64-efi/videotest.mod: OK
./boot/grub/x86_64-efi/gettext.mod: OK
./boot/grub/x86_64-efi/iorw.mod: OK
./boot/grub/x86_64-efi/acpi.mod: OK
./boot/grub/x86_64-efi/part_sun.mod: OK
./boot/grub/x86_64-efi/terminfo.mod: OK
./boot/grub/x86_64-efi/minix3_be.mod: OK
./boot/grub/x86_64-efi/ohci.mod: OK
./boot/grub/x86_64-efi/gcry_arcfour.mod: OK
./boot/grub/x86_64-efi/raid6rec.mod: OK
./boot/grub/x86_64-efi/gfxmenu.mod: OK
./boot/grub/x86_64-efi/xnu_uuid_test.mod: OK
./boot/grub/x86_64-efi/morse.mod: OK
./boot/grub/x86_64-efi/efi_uga.mod: OK
./boot/grub/x86_64-efi/part_apple.mod: OK
./boot/grub/x86_64-efi/video_bochs.mod: OK
./boot/grub/x86_64-efi/dm_nv.mod: OK
./boot/grub/x86_64-efi/gcry_camellia.mod: OK
./boot/grub/x86_64-efi/multiboot2.mod: OK
./boot/grub/x86_64-efi/bitmap.mod: OK
./boot/grub/x86_64-efi/part_plan.mod: OK
./boot/grub/x86_64-efi/usb_keyboard.mod: OK
./boot/grub/x86_64-efi/efifwsetup.mod: OK
./boot/grub/x86_64-efi/part_amiga.mod: OK
./boot/grub/x86_64-efi/parttool.lst: OK
./boot/grub/x86_64-efi/boot.mod: OK
./boot/grub/x86_64-efi/hfs.mod: OK
./boot/grub/x86_64-efi/eval.mod: OK
./boot/grub/x86_64-efi/partmap.lst: OK
./boot/grub/x86_64-efi/adler32.mod: OK
./boot/grub/x86_64-efi/btrfs.mod: OK
./boot/grub/x86_64-efi/gcry_serpent.mod: OK
./boot/grub/x86_64-efi/setjmp_test.mod: OK
./boot/grub/x86_64-efi/cpio_be.mod: OK
./boot/grub/x86_64-efi/tftp.mod: OK
./boot/grub/x86_64-efi/lsefi.mod: OK
./boot/grub/x86_64-efi/xnu_uuid.mod: OK
./boot/grub/x86_64-efi/test.mod: OK
./boot/grub/x86_64-efi/syslinuxcfg.mod: OK
./boot/grub/x86_64-efi/test_blockarg.mod: OK
./boot/grub/x86_64-efi/part_msdos.mod: OK
./boot/grub/x86_64-efi/datetime.mod: OK
./boot/grub/x86_64-efi/keystatus.mod: OK
./boot/grub/x86_64-efi/password.mod: OK
./boot/grub/x86_64-efi/lsefimmap.mod: OK
./boot/grub/x86_64-efi/halt.mod: OK
./boot/grub/x86_64-efi/luks.mod: OK
./boot/grub/x86_64-efi/video.lst: OK
./boot/grub/x86_64-efi/macbless.mod: OK
./boot/grub/x86_64-efi/geli.mod: OK
./boot/grub/x86_64-efi/gcry_tiger.mod: OK
./boot/grub/x86_64-efi/gcry_rmd160.mod: OK
./boot/grub/x86_64-efi/part_sunpc.mod: OK
./boot/grub/x86_64-efi/raid5rec.mod: OK
./boot/grub/x86_64-efi/lspci.mod: OK
./boot/grub/x86_64-efi/terminal.lst: OK
./boot/grub/x86_64-efi/crypto.lst: OK
./boot/grub/x86_64-efi/jpeg.mod: OK
./boot/grub/x86_64-efi/video_fb.mod: OK
./boot/grub/x86_64-efi/datehook.mod: OK
./boot/grub/x86_64-efi/cbtable.mod: OK
./boot/grub/x86_64-efi/mpi.mod: OK
./boot/grub/x86_64-efi/gcry_rijndael.mod: OK
./boot/grub/x86_64-efi/videoinfo.mod: OK
./boot/grub/x86_64-efi/file.mod: OK
./boot/grub/x86_64-efi/testload.mod: OK
./boot/grub/x86_64-efi/gcry_twofish.mod: OK
./boot/grub/x86_64-efi/lsefisystab.mod: OK
./boot/grub/x86_64-efi/usbserial_usbdebug.mod: OK
./boot/grub/x86_64-efi/xfs.mod: OK
./boot/grub/x86_64-efi/minix3.mod: OK
./boot/grub/x86_64-efi/ntfscomp.mod: OK
./boot/grub/x86_64-efi/minix2.mod: OK
./boot/grub/x86_64-efi/uhci.mod: OK
./boot/grub/x86_64-efi/testspeed.mod: OK
./boot/grub/x86_64-efi/jfs.mod: OK
./boot/grub/x86_64-efi/help.mod: OK
./boot/grub/x86_64-efi/offsetio.mod: OK
./boot/grub/x86_64-efi/videotest_checksum.mod: OK
./boot/grub/x86_64-efi/video_colors.mod: OK
./boot/grub/x86_64-efi/usb.mod: OK
./boot/grub/x86_64-efi/zfscrypt.mod: OK
./boot/grub/x86_64-efi/setpci.mod: OK
./boot/grub/x86_64-efi/diskfilter.mod: OK
./boot/grub/x86_64-efi/cat.mod: OK
./boot/grub/x86_64-efi/minicmd.mod: OK
./boot/grub/x86_64-efi/msdospart.mod: OK
./boot/grub/x86_64-efi/part_bsd.mod: OK
./boot/grub/x86_64-efi/gcry_rsa.mod: OK
./boot/grub/x86_64-efi/exfctest.mod: OK
./boot/grub/x86_64-efi/lvm.mod: OK
./boot/grub/x86_64-efi/progress.mod: OK
./boot/grub/x86_64-efi/gcry_sha512.mod: OK
./boot/grub/x86_64-efi/romfs.mod: OK
./boot/grub/x86_64-efi/gfxterm_menu.mod: OK
./boot/grub/x86_64-efi/ufs1_be.mod: OK
./boot/grub/x86_64-efi/newc.mod: OK
./boot/grub/x86_64-efi/true.mod: OK
./boot/grub/x86_64-efi/aout.mod: OK
./boot/grub/x86_64-efi/gfxterm_background.mod: OK
./boot/grub/x86_64-efi/gcry_md4.mod: OK
./boot/grub/x86_64-efi/verify.mod: OK
./boot/grub/x86_64-efi/ehci.mod: OK
./boot/grub/x86_64-efi/video.mod: OK
./boot/grub/x86_64-efi/http.mod: OK
./boot/grub/x86_64-efi/gcry_des.mod: OK
./boot/grub/x86_64-efi/cryptodisk.mod: OK
./boot/grub/x86_64-efi/usbserial_common.mod: OK
./boot/grub/x86_64-efi/backtrace.mod: OK
./boot/grub/x86_64-efi/fat.mod: OK
./boot/grub/x86_64-efi/xnu.mod: OK
./boot/grub/x86_64-efi/lssal.mod: OK
./boot/grub/x86_64-efi/efinet.mod: OK
./boot/grub/x86_64-efi/div_test.mod: OK
./boot/grub/x86_64-efi/grub.cfg: OK
./boot/grub/x86_64-efi/crc64.mod: OK
./boot/grub/x86_64-efi/pcidump.mod: OK
./boot/grub/x86_64-efi/date.mod: OK
./boot/grub/x86_64-efi/parttool.mod: OK
./boot/grub/x86_64-efi/ldm.mod: OK
./boot/grub/x86_64-efi/gcry_sha1.mod: OK
./boot/grub/x86_64-efi/memrw.mod: OK
./boot/grub/x86_64-efi/gcry_crc.mod: OK
./boot/grub/x86_64-efi/png.mod: OK
./boot/grub/x86_64-efi/hfspluscomp.mod: OK
./boot/grub/x86_64-efi/hexdump.mod: OK
./boot/grub/x86_64-efi/ntfs.mod: OK
./boot/grub/x86_64-efi/keylayouts.mod: OK
./boot/grub/x86_64-efi/gcry_md5.mod: OK
./boot/grub/x86_64-efi/gcry_dsa.mod: OK
./boot/grub/x86_64-efi/bfs.mod: OK
./boot/grub/x86_64-efi/usbserial_ftdi.mod: OK
./boot/grub/x86_64-efi/sleep_test.mod: OK
./boot/grub/x86_64-efi/efi_gop.mod: OK
./boot/grub/x86_64-efi/gcry_whirlpool.mod: OK
./boot/grub/x86_64-efi/lzopio.mod: OK
./boot/grub/x86_64-efi/at_keyboard.mod: OK
./boot/grub/x86_64-efi/gptsync.mod: OK
./boot/grub/x86_64-efi/minix2_be.mod: OK
./boot/grub/x86_64-efi/relocator.mod: OK
./boot/grub/x86_64-efi/hashsum.mod: OK
./boot/grub/x86_64-efi/usbserial_pl2303.mod: OK
./boot/grub/x86_64-efi/mdraid09.mod: OK
./boot/grub/x86_64-efi/ata.mod: OK
./boot/grub/x86_64-efi/ufs1.mod: OK
./boot/grub/x86_64-efi/procfs.mod: OK
./boot/grub/x86_64-efi/elf.mod: OK
./boot/grub/x86_64-efi/gfxterm.mod: OK
./boot/grub/x86_64-efi/cpio.mod: OK
./boot/grub/x86_64-efi/ls.mod: OK
./boot/grub/x86_64-efi/mmap.mod: OK
./boot/grub/x86_64-efi/odc.mod: OK
./boot/grub/x86_64-efi/hfsplus.mod: OK
./boot/grub/x86_64-efi/crypto.mod: OK
./boot/grub/x86_64-efi/gcry_idea.mod: OK
./boot/grub/x86_64-efi/net.mod: OK
./boot/grub/x86_64-efi/gcry_rfc2268.mod: OK
./boot/grub/x86_64-efi/legacycfg.mod: OK
./boot/grub/x86_64-efi/pbkdf2_test.mod: OK
./boot/grub/x86_64-efi/cpuid.mod: OK
./boot/grub/x86_64-efi/bsd.mod: OK
./boot/grub/x86_64-efi/part_dvh.mod: OK
./boot/grub/x86_64-efi/sleep.mod: OK
./boot/grub/x86_64-efi/fixvideo.mod: OK
./boot/grub/x86_64-efi/setjmp.mod: OK
./boot/grub/x86_64-efi/read.mod: OK
./boot/grub/x86_64-efi/macho.mod: OK
./boot/grub/x86_64-efi/gcry_blowfish.mod: OK
./boot/grub/x86_64-efi/squash4.mod: OK
./boot/grub/x86_64-efi/multiboot.mod: OK
./boot/grub/x86_64-efi/password_pbkdf2.mod: OK
./boot/grub/x86_64-efi/ext2.mod: OK
./boot/grub/x86_64-efi/bitmap_scale.mod: OK
./boot/grub/x86_64-efi/archelp.mod: OK
./boot/grub/x86_64-efi/moddep.lst: OK
./boot/grub/x86_64-efi/mdraid1x.mod: OK
./boot/grub/x86_64-efi/reiserfs.mod: OK
./boot/grub/x86_64-efi/cmp.mod: OK
./boot/grub/x86_64-efi/fs.lst: OK
./boot/grub/x86_64-efi/loadbios.mod: OK
./boot/grub/x86_64-efi/linuxefi.mod: OK
./boot/grub/x86_64-efi/hdparm.mod: OK
./boot/grub/x86_64-efi/signature_test.mod: OK
./boot/grub/x86_64-efi/cbtime.mod: OK
./boot/grub/x86_64-efi/cbmemc.mod: OK
./boot/grub/x86_64-efi/command.lst: OK
./boot/grub/x86_64-efi/scsi.mod: OK
./boot/grub/x86_64-efi/tr.mod: OK
./boot/grub/x86_64-efi/play.mod: OK
./boot/grub/x86_64-efi/ufs2.mod: OK
./boot/grub/x86_64-efi/mdraid09_be.mod: OK
./boot/grub/x86_64-efi/loadenv.mod: OK
./boot/grub/x86_64-efi/all_video.mod: OK
./boot/grub/x86_64-efi/linux16.mod: OK
./boot/grub/x86_64-efi/xzio.mod: OK
./boot/grub/x86_64-efi/font.mod: OK
./boot/grub/x86_64-efi/ahci.mod: OK
./boot/grub/x86_64-efi/time.mod: OK
./boot/grub/x86_64-efi/part_dfly.mod: OK
./boot/grub/x86_64-efi/appleldr.mod: OK
./boot/grub/x86_64-efi/cs5536.mod: OK
./boot/grub/x86_64-efi/linux.mod: OK
./boot/grub/x86_64-efi/gcry_cast5.mod: OK
./boot/grub/x86_64-efi/reboot.mod: OK
./boot/grub/x86_64-efi/lsmmap.mod: OK
./boot/grub/x86_64-efi/gzio.mod: OK
./boot/grub/x86_64-efi/usbtest.mod: OK
./boot/grub/x86_64-efi/legacy_password_test.mod: OK
./boot/grub/x86_64-efi/bufio.mod: OK
./boot/grub/x86_64-efi/udf.mod: OK
./boot/grub/x86_64-efi/pbkdf2.mod: OK
./boot/grub/x86_64-efi/video_cirrus.mod: OK
./boot/grub/x86_64-efi/nativedisk.mod: OK
./boot/grub/x86_64-efi/disk.mod: OK
./boot/grub/x86_64-efi/cbfs.mod: OK
./boot/grub/x86_64-efi/cmdline_cat_test.mod: OK
./boot/grub/x86_64-efi/regexp.mod: OK
./boot/grub/x86_64-efi/minix_be.mod: OK
./boot/grub/x86_64-efi/priority_queue.mod: OK
./boot/grub/x86_64-efi/trig.mod: OK
./boot/grub/x86_64-efi/tga.mod: OK
./boot/grub/x86_64-efi/usbms.mod: OK
./boot/grub/x86_64-efi/terminal.mod: OK
./boot/grub/x86_64-efi/gcry_seed.mod: OK
./boot/grub/x86_64-efi/exfat.mod: OK
./boot/grub/x86_64-efi/serial.mod: OK
./boot/grub/x86_64-efi/probe.mod: OK
./boot/grub/x86_64-efi/part_gpt.mod: OK
./boot/grub/efi.img: OK
./boot/grub/grub.cfg: OK
./boot/grub/loopback.cfg: OK
./boot/grub/font.pf2: OK
./casper/filesystem.size: OK
./casper/filesystem.manifest: OK
./casper/filesystem.squashfs: OK
./casper/filesystem.squashfs.gpg: OK
./casper/initrd.lz: OK
./casper/vmlinuz.efi: OK
./casper/filesystem.manifest-remove: OK
./README.diskdefines: OK
./dists/yakkety/restricted/binary-i386/Release: OK
./dists/yakkety/restricted/binary-i386/Packages.gz: OK
./dists/yakkety/restricted/binary-amd64/Release: OK
./dists/yakkety/restricted/binary-amd64/Packages.gz: OK
./dists/yakkety/Release: OK
./dists/yakkety/Release.gpg: OK
./dists/yakkety/main/binary-i386/Release: OK
./dists/yakkety/main/binary-i386/Packages.gz: OK
./dists/yakkety/main/binary-amd64/Release: OK
./dists/yakkety/main/binary-amd64/Packages.gz: OK
./install/mt86plus: OK
hugh@yakkety-laptop:/media/hugh/Ubuntu 16.10 amd64$
```

---

### Post by arcanumwall on 2016-10-08
I did it, full success (réussi=success)

```
./pics/red-upperleft.png: Réussi
./pics/red-lowerleft.png: Réussi
./pics/blue-lowerleft.png: Réussi
./pics/logo-50.jpg: Réussi
./pics/blue-upperright.png: Réussi
./pics/blue-lowerright.png: Réussi
./pics/red-lowerright.png: Réussi
./pics/blue-upperleft.png: Réussi
./pics/debian.jpg: Réussi
./pics/red-upperright.png: Réussi
./preseed/ubuntu.seed: Réussi
./preseed/ltsp.seed: Réussi
./preseed/cli.seed: Réussi
./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb: Réussi
./pool/restricted/i/intel-microcode/intel-microcode_3.20151106.1_amd64.deb: Réussi
./pool/restricted/i/iucode-tool/iucode-tool_1.5.1-1_amd64.deb: Réussi
./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu9_amd64.deb: Réussi
./pool/main/l/lupin/lupin-support_0.57_amd64.deb: Réussi
./pool/main/s/shim-signed/shim-signed_1.17~16.04.1+0.8-0ubuntu2_amd64.deb: Réussi
./pool/main/s/shim/shim_0.8-0ubuntu2_amd64.deb: Réussi
./pool/main/s/setserial/setserial_2.17-49_amd64.deb: Réussi
./pool/main/g/grub2/grub-efi-amd64-bin_2.02~beta2-36ubuntu3.1_amd64.deb: Réussi
./pool/main/g/grub2/grub-efi-amd64_2.02~beta2-36ubuntu3.1_amd64.deb: Réussi
./pool/main/g/grub2/grub-efi_2.02~beta2-36ubuntu3.1_amd64.deb: Réussi
./pool/main/g/glibc/libc6-i386_2.23-0ubuntu3_amd64.deb: Réussi
./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.66.1+2.02~beta2-36ubuntu3.1_amd64.deb: Réussi
./pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb: Réussi
./pool/main/b/b43-fwcutter/b43-fwcutter_019-2_amd64.deb: Réussi
./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-7_amd64.deb: Réussi
./pool/main/w/wvstreams/libuniconf4.6_4.6.1-7_amd64.deb: Réussi
./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-7_amd64.deb: Réussi
./pool/main/w/wvdial/wvdial_1.61-4.1_amd64.deb: Réussi
./pool/main/u/user-setup/user-setup_1.63ubuntu4_all.deb: Réussi
./pool/main/u/ubiquity/oem-config-gtk_2.21.63.2_all.deb: Réussi
./pool/main/u/ubiquity/oem-config_2.21.63.2_all.deb: Réussi
./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_113_all.deb: Réussi
./pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11.1_all.deb: Réussi
./.disk/info: Réussi
./.disk/base_installable: Réussi
./.disk/casper-uuid-generic: Réussi
./.disk/cd_type: Réussi
./.disk/release_notes_url: Réussi
./EFI/BOOT/BOOTx64.EFI: Réussi
./EFI/BOOT/grubx64.efi: Réussi
./boot/grub/x86_64-efi/chain.mod: Réussi
./boot/grub/x86_64-efi/blocklist.mod: Réussi
./boot/grub/x86_64-efi/spkmodem.mod: Réussi
./boot/grub/x86_64-efi/loopback.mod: Réussi
./boot/grub/x86_64-efi/pata.mod: Réussi
./boot/grub/x86_64-efi/echo.mod: Réussi
./boot/grub/x86_64-efi/lsacpi.mod: Réussi
./boot/grub/x86_64-efi/gcry_sha256.mod: Réussi
./boot/grub/x86_64-efi/cbls.mod: Réussi
./boot/grub/x86_64-efi/part_acorn.mod: Réussi
./boot/grub/x86_64-efi/videotest.mod: Réussi
./boot/grub/x86_64-efi/gettext.mod: Réussi
./boot/grub/x86_64-efi/iorw.mod: Réussi
./boot/grub/x86_64-efi/acpi.mod: Réussi
./boot/grub/x86_64-efi/part_sun.mod: Réussi
./boot/grub/x86_64-efi/terminfo.mod: Réussi
./boot/grub/x86_64-efi/minix3_be.mod: Réussi
./boot/grub/x86_64-efi/ohci.mod: Réussi
./boot/grub/x86_64-efi/gcry_arcfour.mod: Réussi
./boot/grub/x86_64-efi/raid6rec.mod: Réussi
./boot/grub/x86_64-efi/gfxmenu.mod: Réussi
./boot/grub/x86_64-efi/xnu_uuid_test.mod: Réussi
./boot/grub/x86_64-efi/morse.mod: Réussi
./boot/grub/x86_64-efi/efi_uga.mod: Réussi
./boot/grub/x86_64-efi/part_apple.mod: Réussi
./boot/grub/x86_64-efi/video_bochs.mod: Réussi
./boot/grub/x86_64-efi/dm_nv.mod: Réussi
./boot/grub/x86_64-efi/gcry_camellia.mod: Réussi
./boot/grub/x86_64-efi/multiboot2.mod: Réussi
./boot/grub/x86_64-efi/bitmap.mod: Réussi
./boot/grub/x86_64-efi/part_plan.mod: Réussi
./boot/grub/x86_64-efi/usb_keyboard.mod: Réussi
./boot/grub/x86_64-efi/efifwsetup.mod: Réussi
./boot/grub/x86_64-efi/part_amiga.mod: Réussi
./boot/grub/x86_64-efi/parttool.lst: Réussi
./boot/grub/x86_64-efi/boot.mod: Réussi
./boot/grub/x86_64-efi/hfs.mod: Réussi
./boot/grub/x86_64-efi/eval.mod: Réussi
./boot/grub/x86_64-efi/partmap.lst: Réussi
./boot/grub/x86_64-efi/adler32.mod: Réussi
./boot/grub/x86_64-efi/btrfs.mod: Réussi
./boot/grub/x86_64-efi/gcry_serpent.mod: Réussi
./boot/grub/x86_64-efi/setjmp_test.mod: Réussi
./boot/grub/x86_64-efi/cpio_be.mod: Réussi
./boot/grub/x86_64-efi/tftp.mod: Réussi
./boot/grub/x86_64-efi/lsefi.mod: Réussi
./boot/grub/x86_64-efi/xnu_uuid.mod: Réussi
./boot/grub/x86_64-efi/test.mod: Réussi
./boot/grub/x86_64-efi/syslinuxcfg.mod: Réussi
./boot/grub/x86_64-efi/test_blockarg.mod: Réussi
./boot/grub/x86_64-efi/part_msdos.mod: Réussi
./boot/grub/x86_64-efi/datetime.mod: Réussi
./boot/grub/x86_64-efi/keystatus.mod: Réussi
./boot/grub/x86_64-efi/password.mod: Réussi
./boot/grub/x86_64-efi/lsefimmap.mod: Réussi
./boot/grub/x86_64-efi/halt.mod: Réussi
./boot/grub/x86_64-efi/luks.mod: Réussi
./boot/grub/x86_64-efi/video.lst: Réussi
./boot/grub/x86_64-efi/macbless.mod: Réussi
./boot/grub/x86_64-efi/geli.mod: Réussi
./boot/grub/x86_64-efi/gcry_tiger.mod: Réussi
./boot/grub/x86_64-efi/gcry_rmd160.mod: Réussi
./boot/grub/x86_64-efi/part_sunpc.mod: Réussi
./boot/grub/x86_64-efi/raid5rec.mod: Réussi
./boot/grub/x86_64-efi/lspci.mod: Réussi
./boot/grub/x86_64-efi/terminal.lst: Réussi
./boot/grub/x86_64-efi/crypto.lst: Réussi
./boot/grub/x86_64-efi/jpeg.mod: Réussi
./boot/grub/x86_64-efi/video_fb.mod: Réussi
./boot/grub/x86_64-efi/datehook.mod: Réussi
./boot/grub/x86_64-efi/cbtable.mod: Réussi
./boot/grub/x86_64-efi/mpi.mod: Réussi
./boot/grub/x86_64-efi/gcry_rijndael.mod: Réussi
./boot/grub/x86_64-efi/videoinfo.mod: Réussi
./boot/grub/x86_64-efi/file.mod: Réussi
./boot/grub/x86_64-efi/testload.mod: Réussi
./boot/grub/x86_64-efi/gcry_twofish.mod: Réussi
./boot/grub/x86_64-efi/lsefisystab.mod: Réussi
./boot/grub/x86_64-efi/usbserial_usbdebug.mod: Réussi
./boot/grub/x86_64-efi/xfs.mod: Réussi
./boot/grub/x86_64-efi/minix3.mod: Réussi
./boot/grub/x86_64-efi/ntfscomp.mod: Réussi
./boot/grub/x86_64-efi/minix2.mod: Réussi
./boot/grub/x86_64-efi/uhci.mod: Réussi
./boot/grub/x86_64-efi/testspeed.mod: Réussi
./boot/grub/x86_64-efi/jfs.mod: Réussi
./boot/grub/x86_64-efi/help.mod: Réussi
./boot/grub/x86_64-efi/offsetio.mod: Réussi
./boot/grub/x86_64-efi/videotest_checksum.mod: Réussi
./boot/grub/x86_64-efi/video_colors.mod: Réussi
./boot/grub/x86_64-efi/usb.mod: Réussi
./boot/grub/x86_64-efi/zfscrypt.mod: Réussi
./boot/grub/x86_64-efi/setpci.mod: Réussi
./boot/grub/x86_64-efi/diskfilter.mod: Réussi
./boot/grub/x86_64-efi/cat.mod: Réussi
./boot/grub/x86_64-efi/minicmd.mod: Réussi
./boot/grub/x86_64-efi/msdospart.mod: Réussi
./boot/grub/x86_64-efi/part_bsd.mod: Réussi
./boot/grub/x86_64-efi/gcry_rsa.mod: Réussi
./boot/grub/x86_64-efi/exfctest.mod: Réussi
./boot/grub/x86_64-efi/lvm.mod: Réussi
./boot/grub/x86_64-efi/progress.mod: Réussi
./boot/grub/x86_64-efi/gcry_sha512.mod: Réussi
./boot/grub/x86_64-efi/romfs.mod: Réussi
./boot/grub/x86_64-efi/gfxterm_menu.mod: Réussi
./boot/grub/x86_64-efi/ufs1_be.mod: Réussi
./boot/grub/x86_64-efi/newc.mod: Réussi
./boot/grub/x86_64-efi/true.mod: Réussi
./boot/grub/x86_64-efi/aout.mod: Réussi
./boot/grub/x86_64-efi/gfxterm_background.mod: Réussi
./boot/grub/x86_64-efi/gcry_md4.mod: Réussi
./boot/grub/x86_64-efi/verify.mod: Réussi
./boot/grub/x86_64-efi/ehci.mod: Réussi
./boot/grub/x86_64-efi/video.mod: Réussi
./boot/grub/x86_64-efi/http.mod: Réussi
./boot/grub/x86_64-efi/gcry_des.mod: Réussi
./boot/grub/x86_64-efi/cryptodisk.mod: Réussi
./boot/grub/x86_64-efi/usbserial_common.mod: Réussi
./boot/grub/x86_64-efi/backtrace.mod: Réussi
./boot/grub/x86_64-efi/fat.mod: Réussi
./boot/grub/x86_64-efi/xnu.mod: Réussi
./boot/grub/x86_64-efi/lssal.mod: Réussi
./boot/grub/x86_64-efi/efinet.mod: Réussi
./boot/grub/x86_64-efi/div_test.mod: Réussi
./boot/grub/x86_64-efi/grub.cfg: Réussi
./boot/grub/x86_64-efi/crc64.mod: Réussi
./boot/grub/x86_64-efi/pcidump.mod: Réussi
./boot/grub/x86_64-efi/date.mod: Réussi
./boot/grub/x86_64-efi/parttool.mod: Réussi
./boot/grub/x86_64-efi/ldm.mod: Réussi
./boot/grub/x86_64-efi/gcry_sha1.mod: Réussi
./boot/grub/x86_64-efi/memrw.mod: Réussi
./boot/grub/x86_64-efi/gcry_crc.mod: Réussi
./boot/grub/x86_64-efi/png.mod: Réussi
./boot/grub/x86_64-efi/hfspluscomp.mod: Réussi
./boot/grub/x86_64-efi/hexdump.mod: Réussi
./boot/grub/x86_64-efi/ntfs.mod: Réussi
./boot/grub/x86_64-efi/keylayouts.mod: Réussi
./boot/grub/x86_64-efi/gcry_md5.mod: Réussi
./boot/grub/x86_64-efi/gcry_dsa.mod: Réussi
./boot/grub/x86_64-efi/bfs.mod: Réussi
./boot/grub/x86_64-efi/usbserial_ftdi.mod: Réussi
./boot/grub/x86_64-efi/sleep_test.mod: Réussi
./boot/grub/x86_64-efi/efi_gop.mod: Réussi
./boot/grub/x86_64-efi/gcry_whirlpool.mod: Réussi
./boot/grub/x86_64-efi/lzopio.mod: Réussi
./boot/grub/x86_64-efi/at_keyboard.mod: Réussi
./boot/grub/x86_64-efi/gptsync.mod: Réussi
./boot/grub/x86_64-efi/minix2_be.mod: Réussi
./boot/grub/x86_64-efi/relocator.mod: Réussi
./boot/grub/x86_64-efi/hashsum.mod: Réussi
./boot/grub/x86_64-efi/usbserial_pl2303.mod: Réussi
./boot/grub/x86_64-efi/mdraid09.mod: Réussi
./boot/grub/x86_64-efi/ata.mod: Réussi
./boot/grub/x86_64-efi/ufs1.mod: Réussi
./boot/grub/x86_64-efi/procfs.mod: Réussi
./boot/grub/x86_64-efi/elf.mod: Réussi
./boot/grub/x86_64-efi/gfxterm.mod: Réussi
./boot/grub/x86_64-efi/cpio.mod: Réussi
./boot/grub/x86_64-efi/ls.mod: Réussi
./boot/grub/x86_64-efi/mmap.mod: Réussi
./boot/grub/x86_64-efi/odc.mod: Réussi
./boot/grub/x86_64-efi/hfsplus.mod: Réussi
./boot/grub/x86_64-efi/crypto.mod: Réussi
./boot/grub/x86_64-efi/gcry_idea.mod: Réussi
./boot/grub/x86_64-efi/net.mod: Réussi
./boot/grub/x86_64-efi/gcry_rfc2268.mod: Réussi
./boot/grub/x86_64-efi/legacycfg.mod: Réussi
./boot/grub/x86_64-efi/pbkdf2_test.mod: Réussi
./boot/grub/x86_64-efi/cpuid.mod: Réussi
./boot/grub/x86_64-efi/bsd.mod: Réussi
./boot/grub/x86_64-efi/part_dvh.mod: Réussi
./boot/grub/x86_64-efi/sleep.mod: Réussi
./boot/grub/x86_64-efi/fixvideo.mod: Réussi
./boot/grub/x86_64-efi/setjmp.mod: Réussi
./boot/grub/x86_64-efi/read.mod: Réussi
./boot/grub/x86_64-efi/macho.mod: Réussi
./boot/grub/x86_64-efi/gcry_blowfish.mod: Réussi
./boot/grub/x86_64-efi/squash4.mod: Réussi
./boot/grub/x86_64-efi/multiboot.mod: Réussi
./boot/grub/x86_64-efi/password_pbkdf2.mod: Réussi
./boot/grub/x86_64-efi/ext2.mod: Réussi
./boot/grub/x86_64-efi/bitmap_scale.mod: Réussi
./boot/grub/x86_64-efi/archelp.mod: Réussi
./boot/grub/x86_64-efi/moddep.lst: Réussi
./boot/grub/x86_64-efi/mdraid1x.mod: Réussi
./boot/grub/x86_64-efi/reiserfs.mod: Réussi
./boot/grub/x86_64-efi/cmp.mod: Réussi
./boot/grub/x86_64-efi/fs.lst: Réussi
./boot/grub/x86_64-efi/loadbios.mod: Réussi
./boot/grub/x86_64-efi/linuxefi.mod: Réussi
./boot/grub/x86_64-efi/hdparm.mod: Réussi
./boot/grub/x86_64-efi/signature_test.mod: Réussi
./boot/grub/x86_64-efi/cbtime.mod: Réussi
./boot/grub/x86_64-efi/cbmemc.mod: Réussi
./boot/grub/x86_64-efi/command.lst: Réussi
./boot/grub/x86_64-efi/scsi.mod: Réussi
./boot/grub/x86_64-efi/tr.mod: Réussi
./boot/grub/x86_64-efi/play.mod: Réussi
./boot/grub/x86_64-efi/ufs2.mod: Réussi
./boot/grub/x86_64-efi/mdraid09_be.mod: Réussi
./boot/grub/x86_64-efi/loadenv.mod: Réussi
./boot/grub/x86_64-efi/all_video.mod: Réussi
./boot/grub/x86_64-efi/linux16.mod: Réussi
./boot/grub/x86_64-efi/xzio.mod: Réussi
./boot/grub/x86_64-efi/font.mod: Réussi
./boot/grub/x86_64-efi/ahci.mod: Réussi
./boot/grub/x86_64-efi/time.mod: Réussi
./boot/grub/x86_64-efi/part_dfly.mod: Réussi
./boot/grub/x86_64-efi/appleldr.mod: Réussi
./boot/grub/x86_64-efi/cs5536.mod: Réussi
./boot/grub/x86_64-efi/linux.mod: Réussi
./boot/grub/x86_64-efi/gcry_cast5.mod: Réussi
./boot/grub/x86_64-efi/reboot.mod: Réussi
./boot/grub/x86_64-efi/lsmmap.mod: Réussi
./boot/grub/x86_64-efi/gzio.mod: Réussi
./boot/grub/x86_64-efi/usbtest.mod: Réussi
./boot/grub/x86_64-efi/legacy_password_test.mod: Réussi
./boot/grub/x86_64-efi/bufio.mod: Réussi
./boot/grub/x86_64-efi/udf.mod: Réussi
./boot/grub/x86_64-efi/pbkdf2.mod: Réussi
./boot/grub/x86_64-efi/video_cirrus.mod: Réussi
./boot/grub/x86_64-efi/nativedisk.mod: Réussi
./boot/grub/x86_64-efi/disk.mod: Réussi
./boot/grub/x86_64-efi/cbfs.mod: Réussi
./boot/grub/x86_64-efi/cmdline_cat_test.mod: Réussi
./boot/grub/x86_64-efi/regexp.mod: Réussi
./boot/grub/x86_64-efi/minix_be.mod: Réussi
./boot/grub/x86_64-efi/priority_queue.mod: Réussi
./boot/grub/x86_64-efi/trig.mod: Réussi
./boot/grub/x86_64-efi/tga.mod: Réussi
./boot/grub/x86_64-efi/usbms.mod: Réussi
./boot/grub/x86_64-efi/terminal.mod: Réussi
./boot/grub/x86_64-efi/gcry_seed.mod: Réussi
./boot/grub/x86_64-efi/exfat.mod: Réussi
./boot/grub/x86_64-efi/serial.mod: Réussi
./boot/grub/x86_64-efi/probe.mod: Réussi
./boot/grub/x86_64-efi/part_gpt.mod: Réussi
./boot/grub/efi.img: Réussi
./boot/grub/grub.cfg: Réussi
./boot/grub/loopback.cfg: Réussi
./boot/grub/font.pf2: Réussi
./casper/filesystem.size: Réussi
./casper/filesystem.manifest: Réussi
./casper/filesystem.squashfs: Réussi
./casper/filesystem.squashfs.gpg: Réussi
./casper/initrd.lz: Réussi
./casper/vmlinuz.efi: Réussi
./casper/filesystem.manifest-remove: Réussi
./README.diskdefines: Réussi
./dists/xenial/restricted/binary-i386/Release: Réussi
./dists/xenial/restricted/binary-i386/Packages.gz: Réussi
./dists/xenial/restricted/binary-amd64/Release: Réussi
./dists/xenial/restricted/binary-amd64/Packages.gz: Réussi
./dists/xenial/Release: Réussi
./dists/xenial/Release.gpg: Réussi
./dists/xenial/main/binary-i386/Release: Réussi
./dists/xenial/main/binary-i386/Packages.gz: Réussi
./dists/xenial/main/binary-amd64/Release: Réussi
./dists/xenial/main/binary-amd64/Packages.gz: Réussi
./install/mt86plus: Réussi


```

---

### Post by arcanumwall on 2016-10-09
But the updates still not working ... Any other suppositions ?

---

### Post by howefield on 2016-10-09
> **arcanumwall said:**
> I did it, full success (réussi=success)

Yep, would have been surprised to see it fail, can't remember the last bad download or burn I saw, but it is good to know that the media is fine.

> **arcanumwall said:**
> But the updates still not working ... Any other suppositions ?

Can we take a step back and see/understand the repositories that you have in the system ?

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by arcanumwall on 2016-10-09
I obtain 

```
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
grep: /etc/apt/sources.list.d/*: No file or folder of this type.


```

---

### Post by howefield on 2016-10-09
> **arcanumwall said:**
> I obtain ....

Nothing unusual except perhaps for the back-ports.

To rule out the status file being corrupted you could use a copy from before you started having the problem, there should be copies of  the status file in /var/backups/ eg,
(this is a fresh yakkety install so there aren't many, you may have several)

```
hugh@yakkety-laptop:/Data/Yakkety$  ls -al /var/backups
total 2916
drwxr-xr-x  4 root root      4096 Oct  9 09:48 .
drwxr-xr-x 14 root root      4096 Oct  7 08:51 ..
-rw-r--r--  1 root root     81920 Oct  9 09:48 alternatives.tar.0
-rw-r--r--  1 root root      3641 Oct  8 14:18 alternatives.tar.1.gz
-rw-r--r--  1 root root    120254 Oct  8 21:35 apt.extended_states.0
-rw-r--r--  1 root root     13787 Oct  8 14:48 apt.extended_states.1.gz
drwx------  2 root root      4096 Oct  8 14:45 Desktop
-rw-r--r--  1 root root        11 Oct  8 14:01 dpkg.arch.0
-rw-r--r--  1 root root        43 Oct  8 14:01 dpkg.arch.1.gz
-rw-r--r--  1 root root       862 Oct  8 14:04 dpkg.diversions.0
-rw-r--r--  1 root root       299 Oct  8 14:04 dpkg.diversions.1.gz
-rw-r--r--  1 root root       265 Oct  7 08:45 dpkg.statoverride.0
-rw-r--r--  1 root root       190 Oct  7 08:45 dpkg.statoverride.1.gz
-rw-r--r--  1 root root   2159413 Oct  8 21:36 dpkg.status.0
-rw-r--r--  1 root root    539251 Oct  8 14:18 dpkg.status.1.gz
drwx------  2 root root      4096 Oct  8 14:45 .gnome-desktop
-rw-------  1 root root      1047 Oct  8 14:46 group.bak
-rw-------  1 root shadow     875 Oct  8 14:46 gshadow.bak
-rw-------  1 root root      2527 Oct  8 14:28 passwd.bak
-rw-------  1 root shadow    1395 Oct  8 14:28 shadow.bak
hugh@yakkety-laptop:/Data/Yakkety$ 
```

Check that you still have the /var/lib/dpkg/status.bad file created from earlier in the thread so that you have a copy of the original and then..

```
sudo cp /var/backups/dpkg.status.*.gz /var/lib/dpkg/
```
```
sudo gunzip -d /var/lib/dpkg/dpkg.tatus.*.gz
``` 
```
sudo mv /var/lib/dpkg/dpkg.status.* /var/lib/dpkg/status
```

Replace the * with the number in the file name, eg for me that process might look like..

```
hugh@yakkety-laptop:/Data/Yakkety$  sudo cp /var/backups/dpkg.status.1.gz /var/lib/dpkg/
[sudo] password for hugh: 
hugh@yakkety-laptop:/Data/Yakkety$  sudo gunzip -d /var/lib/dpkg/dpkg.status.1.gz
hugh@yakkety-laptop:/Data/Yakkety$  sudo mv /var/lib/dpkg/dpkg.status.1 /var/lib/dpkg/status
hugh@yakkety-laptop:/Data/Yakkety$ 
```

If this doesn't work the status file is probably ok, and you are back to the .list files that were tried earlier, sometimes it takes a few tries to get it working, but it might be worth going into the Software & Updates application and unchecking every repository in each of the relevant tabs, make a note of what you do here so that you can revert back, reload the software sources when you close out and then go back in and check off the repositories to enable them again.

---

### Post by arcanumwall on 2016-10-09
> **howefield said:**
> 

Replace the * with the number in the file name, eg for me that process might look like..


I don't understand. The code give me 

```
total 1880
drwxr-xr-x  2 root root      4096 oct.   8 02:27 .
drwxr-xr-x 14 root root      4096 juil. 19 22:54 ..
-rw-r--r--  1 root root     71680 oct.   7 12:48 alternatives.tar.0
-rw-r--r--  1 root root     95897 oct.   7 12:41 apt.extended_states.0
-rw-r--r--  1 root root        11 oct.   7 12:36 dpkg.arch.0
-rw-r--r--  1 root root      1044 oct.   7 12:37 dpkg.diversions.0
-rw-r--r--  1 root root       228 juil. 19 22:49 dpkg.statoverride.0
-rw-r--r--  1 root root   1716212 oct.   7 12:41 dpkg.status.0
-rw-------  1 root root       991 oct.   7 12:36 group.bak
-rw-------  1 root shadow     831 oct.   7 12:36 gshadow.bak
-rw-------  1 root root      2243 oct.   7 12:36 passwd.bak
-rw-------  1 root shadow    1247 oct.   7 12:36 shadow.bak


```

But i don't have any [...]status.*.gz  . The only number that i have is 0 but there is no .gz after. Does it matter? Which number shall I use ?

---

### Post by howefield on 2016-10-09
> **arcanumwall said:**
> But i don't have any [...]status.*.gz  . The only number that i have is 0 but there is no .gz after. Does it matter? Which number shall I use ?

Just means that you use the dpkg.status.0 file, but obviously you won't have to unzip, so miss that step out. I wouldn't think this will work with such a recent backup file but certainly worth a try.

---

### Post by arcanumwall on 2016-10-09
that works but it doesn't copy the file in /var/lib/dpgk so when I do 

```
 sudo mv /var/lib/dpkg/dpkg.status.0 /var/lib/dpkg/status

```

It returns me 

```
mv: cannot evaluate '/var/lib/dpkg/dpkg.status.0': no file or folder of this type.


```

I tried 
```
ls /var/lib/dpgk


```

Which returns me 

```
 /var/lib/dpgk


```

and 

```
sudo mv /var/lib/backups/dpkg.status.0 /var/lib/dpkg/status


```

but i get 

```
mv: cannot evaluate '/var/lib/backups/dpkg.status.0': no file or folder of this type.


```

I'm a bit lost with those commands ... :/

---

### Post by howefield on 2016-10-09
> **arcanumwall said:**
> I'm a bit lost with those commands ... :/

Yes, I can see that with the typos, dpgk instead of dpkg and messed up folder paths, ect. Give it a break and go back to it when fresher :)

Try this..
```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/
```
```
sudo mv /var/lib/dpkg/dpkg.status.0 /var/lib/dpkg/status
```

---

### Post by arcanumwall on 2016-10-10
So i did, no problem. (yes a break was a good idea ^^' ) I tried a   apt-get update then. (hope I shall not avoid this) and I get :

```
Atteint:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Réception de:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95,7 kB]
Atteint:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Atteint:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Réception de:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [396 kB]
Réception de:6 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [390 kB]
Réception de:7 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [335 kB]
Réception de:8 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [331 kB]
1 547 ko réceptionnés en 0s (2 795 ko/s)                 
Reading of packages list... Error !
E: Malformed Description-md5 line; includes invalid character 'ca8}8a8767890b9bc5abd350a2cbf3ff'
E: Malformed Description-md5 line; includes invalid character '8f3af546b28&#65533;115a3c8d4812a2034cce'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '&#65533;6c3d7511f54eecaab84089704084b262'
E: Problem parsing dependency Depends
E: Error appends while process of python-wxgtk-media3.0 (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
E: The packages lists or the file « status » can not be reading or analyzed.
```

---

### Post by ubfan1 on 2016-10-10
So, three bad lines (different ones, from the original report) apparently in the 
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
file.  Why don't you try the French repository at fr.archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
instead?

---

### Post by arcanumwall on 2016-10-10
> **ubfan1 said:**
>   Why don't you try the French repository at fr.archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
instead?

What shall I do for that ?

---

### Post by arcanumwall on 2016-10-10
Ok so! 
I switched the downloading server for the French one. (I already tried it at the beginning ) It works this time, I have been able to run an apt-get update and an apt-get upgrade. I then ran the upgrade manager but I get one error message. Anyway upgrades get finished. I then rebooted the computer, twice. And from the second time I haven't been able to go further the first black screen. So I have reboot with my USB key and i have make a new installation. The first failed, but the second get perfect. I had just proceed to the upgrades with the upgrade manager, then reboot and everything seems going well. I can hear music, watch movies etc ... 
So whatever append with the previous installation I'm happy to tell you that everything seem to going well ! :D

I want to thank you three for your help and your attention!

I just have a question, when shall I use apt-get update and an apt-get upgrade ? Like ... once a month or ... ?

cheers

---

### Post by howefield on 2016-10-10
> **arcanumwall said:**
> So whatever append with the previous installation I'm happy to tell you that everything seem to going well ! :D

Terrific and well done, even if it took a fresh install.

> I just have a question, when shall I use apt-get update and an apt-get upgrade ? Like ... once a month or ... ?

sudo apt update every time you want to install a package or application.

Upgrades should happen automatically if you have left the defaults alone due to unattended-upgrades (which is a new process with 16.04) and should keep the already installed packages updated or let you know if it needs your intervention. If you switch automatic updates off, then I'd suggest whatever you are comfortable with, I generally update weekly if there is anything substantial.

After an apt update you will be told how many (if any at all) packages can be upgraded, and apt list --upgradable will tell you what the packages are, eg after an apt update I am told there are 8 packages on this system that can be upgraded.. so I can decide how urgent they are by looking

```
hugh@yakkety-laptop:~$ apt list --upgradable
Listing... Done
base-files/yakkety 9.6ubuntu5 amd64 [upgradable from: 9.6ubuntu4]
language-pack-en/yakkety,yakkety 1:16.10+20161009 all [upgradable from: 1:16.10+20160929]
language-pack-en-base/yakkety,yakkety 1:16.10+20161009 all [upgradable from: 1:16.10+20160915]
language-pack-gnome-en/yakkety,yakkety 1:16.10+20161009 all [upgradable from: 1:16.10+20160929]
language-pack-gnome-en-base/yakkety,yakkety 1:16.10+20161009 all [upgradable from: 1:16.10+20160915]
network-manager-openvpn/yakkety 1.2.6-2ubuntu1 amd64 [upgradable from: 1.1.93-1ubuntu1]
python-cairo/yakkety 1.8.8-2.1 amd64 [upgradable from: 1.8.8-2]
skypeforlinux/stable 1.10.0.1 amd64 [upgradable from: 1.9.0.2]
hugh@yakkety-laptop:~$ 
```

---

### Post by ubfan1 on 2016-10-10
You probably will get notices of when new updates are available.  Then you can just run the gui Software Updater, or apt-get update then apt-get install,  not the apt-get upgrade.

---

### Post by arcanumwall on 2016-10-10
Okay thank you :)

---

