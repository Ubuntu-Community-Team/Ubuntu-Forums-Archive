---
title: "Can't boot from DVD - &quot;No valid operating system&quot;?"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by luke37 on 2014-09-05
[SIZE=2][FONT=arial]Hey, guys. I'm trying to install Ubuntu [/FONT][/SIZE][COLOR=#333333][FONT=arial]14.04.1 LTS from a DVD but I'm having difficulties.

I burned the image file to a DVD using InfraRecorder, following the "How to burn a DVD on Windows" guide, and when I looked at the DVD I saw the following directories and files:
.disk
boot
casper
dists
EFI
install
isolinux
pics
pool
preseed
autorun.inf
md5sum.txt
README.diskdefines
wubi.exe

With the DVD in my drive, I restarted and entered BIOS, then went Startup -> Boot

My boot priority is as follows:
1. ATAPI CD0: HL-DT-ST DVDRAM GU10N-(S2)
2. USB FDD:
3. ATA HDD0:
4. PCI LAN: IBA GE SLOT 00C8 v1351
5. -USB HDD
6. USB CD:
7. ATA HDD1:

I then saved and exited, and Ubuntu didn't boot - the computer booted Windows instead.

I restarted and pressed F12 to enter the boot menu, then selected 1: ATAPI CD0: HL-DT-ST DVDRAM GU10N-(S2)
I was then told that no bootable devices were found, and a list of devices claimed that the ATAPI CD0 didn't boot because it had "No valid operating system". 

I'm using a Lenovo Thinkpad T410, currently running Windows 7 Professional.

Any help would be greatly appreciated. Thanks in advance![/FONT][/COLOR]

---

### Post by QIII on 2014-09-05
Hello!

Did you confirm the md5sum on the .iso you downloaded?

---

### Post by luke37 on 2014-09-05
Sorry, but I don't know how I would do that. If it helps, here are the contents of the md5sum:

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
b31731ea6cdbebe1d02f8193db420886  ./wubi.exe
4feecfaee3fe95e05818dccbedf42155  ./autorun.inf
24ec176894c781355f9ccb08ba69919e  ./preseed/ubuntu.seed
0391854d1af5a015a667f29fa0442e78  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
3a9fca958bc1e3e78acfae7d040b95da  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb
051d08864162eb511ce90b9609481af5  ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu9_amd64.deb
98bd889c61ec21949921e5825050a575  ./pool/main/l/lupin/lupin-support_0.55_amd64.deb
e144f20c14c6251b6cabf7522fb6a8ca  ./pool/main/s/secureboot-db/secureboot-db_1.1_amd64.deb
3456329d8517b8c28844abb83055a48a  ./pool/main/s/shim-signed/shim-signed_1.6+0.4-0ubuntu4_amd64.deb
222bb9b2f22e3ae04bee6615d3c6cd1e  ./pool/main/s/shim/shim_0.4-0ubuntu4_amd64.deb
b373717b1b4406d9b764f53cb0ee7a22  ./pool/main/s/setserial/setserial_2.17-48_amd64.deb
f7517117eb41780c1ead3eae025faffb  ./pool/main/g/grub2/grub-efi_2.02~beta2-9ubuntu1_amd64.deb
ac1ba84f1c2b35ad5c1609db7674be4e  ./pool/main/g/grub2/grub-efi-amd64_2.02~beta2-9ubuntu1_amd64.deb
1377577eb97c9725c45307e9ccd909d8  ./pool/main/g/grub2/grub-efi-amd64-bin_2.02~beta2-9ubuntu1_amd64.deb
7a82f240ddc27d31969cad84a0bae20a  ./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.34.1+2.02~beta2-9ubuntu1_amd64.deb
cf320b21c8873ede3170d63b923c3942  ./pool/main/b/b43-fwcutter/b43-fwcutter_018-2_amd64.deb
c2b74ba7fc6bef59fdfcbafa4ec2f6c7  ./pool/main/e/efibootmgr/efibootmgr_0.5.4-7ubuntu1_amd64.deb
fee6246e273ba9c2ff39385918e3f52a  ./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-7_amd64.deb
10638bcd250ccf702637a64d6c1f21d4  ./pool/main/w/wvstreams/libuniconf4.6_4.6.1-7_amd64.deb
275d85005fe762aa48e8a8103fd5a22d  ./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-7_amd64.deb
b878702b4959ae848ed7568523f35eee  ./pool/main/w/wvdial/wvdial_1.61-4.1_amd64.deb
4e905cb86bc4c05dfe6b8a1a3be2a80c  ./pool/main/u/user-setup/user-setup_1.48ubuntu2_all.deb
9b862ca472084c93baafa2e3f0727d65  ./pool/main/u/ubiquity/oem-config-gtk_2.18.8_all.deb
f4eca10fcfa914f5d4ea171ea5ca315a  ./pool/main/u/ubiquity/oem-config_2.18.8_all.deb
340ad8481023b4530dc7cce08accf50c  ./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_83_all.deb
c061b4c50bcebc9d51f65703f5f8fdaf  ./pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb
856c7401d7d5a63ea231f706c18d9261  ./pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb
fad29881d632a463f5235f399fa65a14  ./pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb
26ce8a65c137c8bd11c5b56629dd297c  ./.disk/info
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
92c544da3f6e27843d0028b83fd80dfd  ./.disk/casper-uuid-generic
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
6a7b9409367e9e6fa2326205e9360be6  ./.disk/release_notes_url
7095619324a9fb786422d7427c056405  ./EFI/BOOT/BOOTx64.EFI
71454781dada38e9c6ef0eaf9ccce642  ./EFI/BOOT/grubx64.efi
ce2c43671b8a353852dd827cb4c5e576  ./boot/grub/x86_64-efi/chain.mod
61585b0d9312966874ec89509334e73c  ./boot/grub/x86_64-efi/blocklist.mod
280ad1780f1cc83ad83b69dd67cf1c92  ./boot/grub/x86_64-efi/spkmodem.mod
a4ee8b359104dbc537d8db6d16d0c8c4  ./boot/grub/x86_64-efi/loopback.mod
355c74b6e3d9eff6337ca3e4f806702d  ./boot/grub/x86_64-efi/pata.mod
bcdde891167f4d726910d5db2d057230  ./boot/grub/x86_64-efi/echo.mod
4ce91a9668f0e140a9cc478db9c069c4  ./boot/grub/x86_64-efi/lsacpi.mod
78f902dbd4c4481cd04d1acbddf201d9  ./boot/grub/x86_64-efi/gcry_sha256.mod
b710e1b53c90fcf663d3068af5b32404  ./boot/grub/x86_64-efi/cbls.mod
3b7b025e07527b50081156f0163d3ab3  ./boot/grub/x86_64-efi/part_acorn.mod
ca21a051081b598b6411a808e20d8080  ./boot/grub/x86_64-efi/videotest.mod
f965f48ae0506bec5c2d6d4ad3e4b986  ./boot/grub/x86_64-efi/gettext.mod
dfd2460a0ca4e27626a5b71e8c48608e  ./boot/grub/x86_64-efi/iorw.mod
68c72aee7ce18c934d43b0767e1b09d6  ./boot/grub/x86_64-efi/acpi.mod
577279f75061488365ec130434f68901  ./boot/grub/x86_64-efi/part_sun.mod
c4e5843c8d9cf5e076184644172032c9  ./boot/grub/x86_64-efi/terminfo.mod
56bbef6320ed9d1a9a256391da773e50  ./boot/grub/x86_64-efi/minix3_be.mod
198901e033be30d1159e5d1a14e282a3  ./boot/grub/x86_64-efi/ohci.mod
0fdc0f214fdfab11572dc36d74e7e31e  ./boot/grub/x86_64-efi/gcry_arcfour.mod
96826017c66da995b713549820499521  ./boot/grub/x86_64-efi/raid6rec.mod
5fb9e4861ed7efd083e52f25b0a1c6c4  ./boot/grub/x86_64-efi/gfxmenu.mod
ffd3a0082b0f690ed1153c8f85856873  ./boot/grub/x86_64-efi/xnu_uuid_test.mod
06dce0da9e6b21c1015170c06d291c22  ./boot/grub/x86_64-efi/morse.mod
3743a9d7047a06b6d6800661ee19512c  ./boot/grub/x86_64-efi/efi_uga.mod
c781a3ed5e21d9c151c4c9be0171bdff  ./boot/grub/x86_64-efi/part_apple.mod
e5374c1e42bdba40eeefc006a7cf995f  ./boot/grub/x86_64-efi/video_bochs.mod
7607eae545ac07102a28d7a860b06d18  ./boot/grub/x86_64-efi/dm_nv.mod
49e3e3b6a73637b9db69273dec8c4ddf  ./boot/grub/x86_64-efi/gcry_camellia.mod
e2cb50eb8ff336456aa4ba04eaf3b676  ./boot/grub/x86_64-efi/multiboot2.mod
b37171189832fe76587ff7706fa8a7ff  ./boot/grub/x86_64-efi/bitmap.mod
9e3f7a7e95391a9c0121b3b8d1ae8238  ./boot/grub/x86_64-efi/part_plan.mod
b7a034681ea6f466e51cd596071587d3  ./boot/grub/x86_64-efi/usb_keyboard.mod
91370ac0389e36f5089a1d3c061c4bb3  ./boot/grub/x86_64-efi/efifwsetup.mod
a7cbedd501db2ea1bf81825dd587fac7  ./boot/grub/x86_64-efi/part_amiga.mod
3190a91d3075032543740d0998971d77  ./boot/grub/x86_64-efi/parttool.lst
9d53ac2364fa4b0db63590647ee9d184  ./boot/grub/x86_64-efi/boot.mod
f0cce4c508fc2cc33400c58fc629ada3  ./boot/grub/x86_64-efi/hfs.mod
1ed60f552a7c9d0865e1aa3a7c7ede60  ./boot/grub/x86_64-efi/eval.mod
02b988d7196362ddf27caaecf35c23dc  ./boot/grub/x86_64-efi/partmap.lst
9000ee7d2ea7d4540528256a29494b27  ./boot/grub/x86_64-efi/adler32.mod
19dfe1267da555868f1bb027de9587bf  ./boot/grub/x86_64-efi/btrfs.mod
f199a55f417366fc4b53fec134078e1b  ./boot/grub/x86_64-efi/gcry_serpent.mod
2dc32a35aca300cc66387a6cd28480c7  ./boot/grub/x86_64-efi/setjmp_test.mod
d77cae1396c9375b84ce23bc696e7e97  ./boot/grub/x86_64-efi/cpio_be.mod
8258180555191e122cefa7f8421f1146  ./boot/grub/x86_64-efi/tftp.mod
b8dab52324a02c1060668ad2308cd659  ./boot/grub/x86_64-efi/lsefi.mod
cea67591e11068c8d8b529d6f166b38e  ./boot/grub/x86_64-efi/xnu_uuid.mod
8a9adf8f7afcf1168afd2777f5813d19  ./boot/grub/x86_64-efi/test.mod
17a6f1aaacc5f455ee77f07e6bd580ba  ./boot/grub/x86_64-efi/syslinuxcfg.mod
ccc93b8bebd3c1bf857707d34cae9806  ./boot/grub/x86_64-efi/test_blockarg.mod
4b153b9dcb6b51617b9a7696e175ce6b  ./boot/grub/x86_64-efi/part_msdos.mod
347af3e5330087cc1d6a131421dad564  ./boot/grub/x86_64-efi/datetime.mod
e9496f20d6b193a756336b442d839c2a  ./boot/grub/x86_64-efi/keystatus.mod
d6995cf275378e474ea331371ff927fe  ./boot/grub/x86_64-efi/password.mod
f8e05502b990c1463a39a04582995a68  ./boot/grub/x86_64-efi/lsefimmap.mod
a0332ae10d19c219e955328e314f7fc3  ./boot/grub/x86_64-efi/halt.mod
85b79d1b808b2af3a5b99857def87a20  ./boot/grub/x86_64-efi/luks.mod
7d86acc3d68833f22603dc5859e8ebdc  ./boot/grub/x86_64-efi/video.lst
7059d12993c155c516b4b8965ccd367d  ./boot/grub/x86_64-efi/macbless.mod
156b5df9c378cf9f3ac9db0556fc0642  ./boot/grub/x86_64-efi/geli.mod
6bc63ee8fb58cdaf5ee09ebb66a004d5  ./boot/grub/x86_64-efi/gcry_tiger.mod
783bb6faa56c599937b6c96fae2c3157  ./boot/grub/x86_64-efi/gcry_rmd160.mod
9fdd48b3ac6358869b19d984f521ac49  ./boot/grub/x86_64-efi/part_sunpc.mod
9154bed5ff5c7c1c3ad9283fbd01d47e  ./boot/grub/x86_64-efi/raid5rec.mod
89b15168b3c32bbda52745972d8bc640  ./boot/grub/x86_64-efi/lspci.mod
098832497928edecd396096490b430de  ./boot/grub/x86_64-efi/terminal.lst
6a3f58db454b17a0a339323b3e134a6b  ./boot/grub/x86_64-efi/crypto.lst
2d616b603d229b4fea00c182c8ae3417  ./boot/grub/x86_64-efi/jpeg.mod
9d7773f1842dabae98879bd8013bcf41  ./boot/grub/x86_64-efi/video_fb.mod
e754099bc116c3c0333b1a057852483c  ./boot/grub/x86_64-efi/datehook.mod
fb655631d0fe90ef1193182d9b04be21  ./boot/grub/x86_64-efi/cbtable.mod
35b4d75a86bfd085fe64a4fd04b4531b  ./boot/grub/x86_64-efi/mpi.mod
d9fb2116fcb7bc40dfba63b0a1ed4eb7  ./boot/grub/x86_64-efi/gcry_rijndael.mod
d3fe2fce5fe53aa46598d54d1b746442  ./boot/grub/x86_64-efi/videoinfo.mod
4701a286d6adf9354675c517dad2bb17  ./boot/grub/x86_64-efi/file.mod
f95eff0e74221194ed1922a9680944ee  ./boot/grub/x86_64-efi/testload.mod
091447bace449c849445ed20b148d3ad  ./boot/grub/x86_64-efi/gcry_twofish.mod
6176bc60f8e061f1f7c633bffceb6b34  ./boot/grub/x86_64-efi/lsefisystab.mod
e45885854accb7709305fc3b2dfe3e1a  ./boot/grub/x86_64-efi/usbserial_usbdebug.mod
451d5efc3d0461726e16b9d430dcb17a  ./boot/grub/x86_64-efi/xfs.mod
7b906086983edd5717cadc37e5767c91  ./boot/grub/x86_64-efi/minix3.mod
90d8453fd6ee6536609b4381ed2573a5  ./boot/grub/x86_64-efi/ntfscomp.mod
9e9ed22b98cca5be6bd94f8be6ddef7c  ./boot/grub/x86_64-efi/minix2.mod
bdc961cdd5507f740d2f2f5f620b9484  ./boot/grub/x86_64-efi/uhci.mod
1da965642d4660292f13fc0fb83c1140  ./boot/grub/x86_64-efi/testspeed.mod
631e53dc6353803b1249e79a9d358a28  ./boot/grub/x86_64-efi/jfs.mod
fc74ecc929110b8e8584275f3ab4078d  ./boot/grub/x86_64-efi/help.mod
9fc2eb728464c1a5c980314e50648dc3  ./boot/grub/x86_64-efi/offsetio.mod
b99ee13b4ded8cef60a850271f994102  ./boot/grub/x86_64-efi/videotest_checksum.mod
c1f45b8bd4be220179b9f379d7f221d0  ./boot/grub/x86_64-efi/video_colors.mod
21fd9b8dab7ad18a6cd23fa68a4c9367  ./boot/grub/x86_64-efi/usb.mod
8a0452bfbf03f2a69348ebe8343f8bef  ./boot/grub/x86_64-efi/zfscrypt.mod
0f4484db2ee6be52f4e15c3669a31d17  ./boot/grub/x86_64-efi/setpci.mod
8d81e2bb32a97141c3e655794c80e065  ./boot/grub/x86_64-efi/diskfilter.mod
7ab1719ae33d2919b9eddfe5d1b5a1ca  ./boot/grub/x86_64-efi/cat.mod
1431e0c586bd6df23732284f93cb7df9  ./boot/grub/x86_64-efi/minicmd.mod
bee7602ce68ad178b29fb40d39cb9a40  ./boot/grub/x86_64-efi/msdospart.mod
020ee62aa2d2d698d453bb7920ee40f5  ./boot/grub/x86_64-efi/part_bsd.mod
e380270beca6803a812c93610f5d0d65  ./boot/grub/x86_64-efi/gcry_rsa.mod
54da471711870f76a2616c1b7bdb58e7  ./boot/grub/x86_64-efi/exfctest.mod
ff2c59417b645173becee478bc0136e4  ./boot/grub/x86_64-efi/lvm.mod
29af580a2e10b62ac314358d1dd5d69d  ./boot/grub/x86_64-efi/progress.mod
52d79ee2b44ae425ac96abfa1b98bc5d  ./boot/grub/x86_64-efi/gcry_sha512.mod
8301d88ae5a382839bd01a2b45280bca  ./boot/grub/x86_64-efi/romfs.mod
fe4bedd035f79cc9e785fcb40da52da0  ./boot/grub/x86_64-efi/gfxterm_menu.mod
4adf119820f8bdb9972590992f023d7e  ./boot/grub/x86_64-efi/ufs1_be.mod
7cdca73c184b61173edb3067a0af2122  ./boot/grub/x86_64-efi/newc.mod
fa6c97fcc632f1a84f4da6f6e0bb0bb9  ./boot/grub/x86_64-efi/true.mod
b111bc49b6f59bf2fa990752d9936955  ./boot/grub/x86_64-efi/aout.mod
011a8895dc0b2f3c0590e984b4cc7456  ./boot/grub/x86_64-efi/gfxterm_background.mod
f2c1c37ded8cdc6a17748c1e83dcd2b0  ./boot/grub/x86_64-efi/gcry_md4.mod
28b3b04c9240510d02d884248983fd57  ./boot/grub/x86_64-efi/verify.mod
0e219d5d6db65b370fbb14d1da1a6f89  ./boot/grub/x86_64-efi/ehci.mod
02e43b5347278f9ca331961e204712bc  ./boot/grub/x86_64-efi/video.mod
3908ebc1c6b2ca205d22a28159c56033  ./boot/grub/x86_64-efi/http.mod
27693098a92f8ea2c8a1068ad6b0fdd7  ./boot/grub/x86_64-efi/gcry_des.mod
8aebd584539c669624b087b3e0ef4c27  ./boot/grub/x86_64-efi/cryptodisk.mod
ee6f179b5c7fb0c72690469ec1d5d45c  ./boot/grub/x86_64-efi/usbserial_common.mod
5cca8dea7ff6b4283cdc593f91bbdc86  ./boot/grub/x86_64-efi/backtrace.mod
a015fcc4a4d947417099a94af78557b4  ./boot/grub/x86_64-efi/fat.mod
9af527788f509bf5c95008927107e819  ./boot/grub/x86_64-efi/xnu.mod
9d69ab8cea3d3b921e046e8fdc688e19  ./boot/grub/x86_64-efi/lssal.mod
b00ddc1e6ec6e428d94d290e45356d69  ./boot/grub/x86_64-efi/efinet.mod
fb08274126fa46ff149fbe523779af4f  ./boot/grub/x86_64-efi/div_test.mod
a105ed65e2f91069ba7d7f6dadf00ee5  ./boot/grub/x86_64-efi/grub.cfg
9cf96a9393a934a3b5f3c47621948ddf  ./boot/grub/x86_64-efi/crc64.mod
6fec03f3dce8838aeb9af95393e1ca16  ./boot/grub/x86_64-efi/pcidump.mod
2c155f93ae6689a5aeb8ebd5d7681cc8  ./boot/grub/x86_64-efi/date.mod
25cad95f21629bb6d6e56c896c2b66ec  ./boot/grub/x86_64-efi/parttool.mod
4db224087084d4434d8b1606d669a44c  ./boot/grub/x86_64-efi/ldm.mod
ea155977e9a49f6630ac2557998a93c0  ./boot/grub/x86_64-efi/gcry_sha1.mod
02bf544b71205a0ac367917567a00126  ./boot/grub/x86_64-efi/memrw.mod
c10af0c2fa8a306aa1bf12c6e4bb2fd7  ./boot/grub/x86_64-efi/gcry_crc.mod
e97b61b1dc7d28047faa90fcb169b31b  ./boot/grub/x86_64-efi/png.mod
e51ad530f3fe271ee65ae577e5f1321f  ./boot/grub/x86_64-efi/hfspluscomp.mod
26167c327751660d6bb3e8e6e795959a  ./boot/grub/x86_64-efi/hexdump.mod
1bb49d6cb58ff69fda6c888f22a4594b  ./boot/grub/x86_64-efi/ntfs.mod
6e7199e85567216e9460e09e951ec22f  ./boot/grub/x86_64-efi/keylayouts.mod
b42b08c8b8e183d83a3ff46ba075779f  ./boot/grub/x86_64-efi/gcry_md5.mod
a6952c664d7c3b85f2ee7bdd26bf923c  ./boot/grub/x86_64-efi/gcry_dsa.mod
c2894c622f86d17c614eb5517527ebb5  ./boot/grub/x86_64-efi/bfs.mod
1668ce1208a52180e88ee9164fb88ca5  ./boot/grub/x86_64-efi/usbserial_ftdi.mod
3b6a7b04f6585e133dc3cba111446a17  ./boot/grub/x86_64-efi/sleep_test.mod
ff26feab517096d1137630c1ba63e838  ./boot/grub/x86_64-efi/efi_gop.mod
cfb5662e930706bf345aa0bece2a03c0  ./boot/grub/x86_64-efi/gcry_whirlpool.mod
8895cf465113033f772ee55389f47426  ./boot/grub/x86_64-efi/lzopio.mod
453cc3bdb221cd6dacf37de4dcd65611  ./boot/grub/x86_64-efi/at_keyboard.mod
3c5cc8706762aefde6ea773677d1572c  ./boot/grub/x86_64-efi/gptsync.mod
70dd8836d0a39b07eefba2f09e454906  ./boot/grub/x86_64-efi/minix2_be.mod
f0cc46303444e7c3302d7071616b2224  ./boot/grub/x86_64-efi/relocator.mod
4c520375161cf1a9c495cf25f9634028  ./boot/grub/x86_64-efi/hashsum.mod
c3f39276779e6baed631615b256ab394  ./boot/grub/x86_64-efi/usbserial_pl2303.mod
fa7328111ca7a2b76a731acc8f1bc074  ./boot/grub/x86_64-efi/mdraid09.mod
4289f952cbd3074b5116e254b952379a  ./boot/grub/x86_64-efi/ata.mod
71136e82cefe6f4c9814c93b470210c1  ./boot/grub/x86_64-efi/ufs1.mod
80a9a7e5e0ad052a93dd3b8930f03919  ./boot/grub/x86_64-efi/procfs.mod
80595cbcb17c628e0594a688cb9039db  ./boot/grub/x86_64-efi/elf.mod
2bd18df7ae0119f0a176225c62293188  ./boot/grub/x86_64-efi/gfxterm.mod
0f26c41fac623c78b97a086de3f97635  ./boot/grub/x86_64-efi/cpio.mod
e5233a7bbdbeb5da6be446f65e070a7d  ./boot/grub/x86_64-efi/ls.mod
4dfb2b2098dcc080e3e4d83a99c1f2cd  ./boot/grub/x86_64-efi/mmap.mod
83e4a1b7f9a11ee80c15fda91e983a19  ./boot/grub/x86_64-efi/odc.mod
55c0c560847b01819d087d79c30b99e5  ./boot/grub/x86_64-efi/hfsplus.mod
ac0c0eca8d830bb2b358aee3ecd54e6e  ./boot/grub/x86_64-efi/crypto.mod
de52bf0023b5718f546c2f0e104de392  ./boot/grub/x86_64-efi/gcry_idea.mod
553ae735c3ad671be441d5f5afbfb127  ./boot/grub/x86_64-efi/net.mod
5bb7aeb39a4063c7c1a0198876272b13  ./boot/grub/x86_64-efi/gcry_rfc2268.mod
deb3a8fbce90d7982dc698676aeb3011  ./boot/grub/x86_64-efi/legacycfg.mod
4839813ab5681acd99782f2c260cf02f  ./boot/grub/x86_64-efi/pbkdf2_test.mod
bfb2beea0bf5b8ab6c5c9a9e94eb94fc  ./boot/grub/x86_64-efi/cpuid.mod
86504fb8ee9b208420a026f6254a79e7  ./boot/grub/x86_64-efi/bsd.mod
62dbac2c50f80160f91d824d206b08ad  ./boot/grub/x86_64-efi/part_dvh.mod
8f8e708910ae7f6dcefee6ea2dd1f5be  ./boot/grub/x86_64-efi/sleep.mod
c56a7b9b6097fb3495202c8320eeff85  ./boot/grub/x86_64-efi/fixvideo.mod
399155545436c4a794e4ed3cfed2f592  ./boot/grub/x86_64-efi/setjmp.mod
ed13ebd79f781e74e5e8a5edb672ed87  ./boot/grub/x86_64-efi/read.mod
62b3e9a0dd514fdb9f2a791fc8d6a88e  ./boot/grub/x86_64-efi/macho.mod
39e3755dcbf6bf1860a4e9267360baa7  ./boot/grub/x86_64-efi/gcry_blowfish.mod
f2ed50946d02389da600dad224910533  ./boot/grub/x86_64-efi/squash4.mod
656343c64ef2b22a1eb79db1f12bbd70  ./boot/grub/x86_64-efi/multiboot.mod
914b1a8a557c746c163d8f1907570496  ./boot/grub/x86_64-efi/password_pbkdf2.mod
d0da934d6bbd8bea8c423ac514529721  ./boot/grub/x86_64-efi/ext2.mod
d2964da9dbb83c388be92d81fcc37bdc  ./boot/grub/x86_64-efi/bitmap_scale.mod
40336e40c05c809cc6db5bd37afa8a13  ./boot/grub/x86_64-efi/archelp.mod
9aafcdfd75a849a6c57c519fac8116d1  ./boot/grub/x86_64-efi/moddep.lst
b75fe21a2ecf02880cfba198abd0146b  ./boot/grub/x86_64-efi/mdraid1x.mod
dfb4402baf3cd742623a71afa8caa5e6  ./boot/grub/x86_64-efi/reiserfs.mod
24c97ac99e781cd0f1386daa97f99fdd  ./boot/grub/x86_64-efi/cmp.mod
eeeda090212fe67f0e81c738a425bc93  ./boot/grub/x86_64-efi/fs.lst
9c18bf1421de412c44fd302ddace0bfd  ./boot/grub/x86_64-efi/loadbios.mod
4c50a26db2f2b01bd2bb367acd732b1e  ./boot/grub/x86_64-efi/linuxefi.mod
9a75e1d2f1399f6362e2d9d71ec2ea13  ./boot/grub/x86_64-efi/hdparm.mod
59256e1b5ca5b25c76660503cd888c52  ./boot/grub/x86_64-efi/signature_test.mod
6f1b53365f1393a965cb927614cf6b27  ./boot/grub/x86_64-efi/cbtime.mod
bc7ffb0e2550ddaeef16b6cf96c10c4b  ./boot/grub/x86_64-efi/cbmemc.mod
d560df0418ccb0f6dcd5d27ba6331bec  ./boot/grub/x86_64-efi/command.lst
d684df42f56a9c0a44f0ee872c8f5785  ./boot/grub/x86_64-efi/scsi.mod
dc30c64a9c60813097dbe267f4bdddb1  ./boot/grub/x86_64-efi/tr.mod
e57265465c41c77ca5662003fede0a4e  ./boot/grub/x86_64-efi/play.mod
0fe973812e80c6d94aa181489181cae8  ./boot/grub/x86_64-efi/ufs2.mod
0defd4731f4c243f707b20a6ce3f614a  ./boot/grub/x86_64-efi/mdraid09_be.mod
c1c65afda8c18ace4f061eee257e5f29  ./boot/grub/x86_64-efi/loadenv.mod
6ddd914d4fff24a3b067fd188cdabf29  ./boot/grub/x86_64-efi/all_video.mod
44e72612b61e9eeac0f9f5be92d35923  ./boot/grub/x86_64-efi/linux16.mod
6ac86ed386af7487c2f95981cd258f8d  ./boot/grub/x86_64-efi/xzio.mod
d5d07f40a93fb6bb47b715a50250b3fb  ./boot/grub/x86_64-efi/font.mod
0bc0b9cd7151d0015e3693ed18fa783f  ./boot/grub/x86_64-efi/ahci.mod
253f8241aeb37f2456f5a4e45f7869d4  ./boot/grub/x86_64-efi/time.mod
afd052f9def132b5435b9f1c3c42cfea  ./boot/grub/x86_64-efi/part_dfly.mod
354f116e6a5fb570333207899d67acd6  ./boot/grub/x86_64-efi/appleldr.mod
d33f95d1fde175e7fdc95d7035f03032  ./boot/grub/x86_64-efi/cs5536.mod
265465b0f59887318b25e92ab6e3c0b1  ./boot/grub/x86_64-efi/linux.mod
f9626075225e3164465933514680f017  ./boot/grub/x86_64-efi/gcry_cast5.mod
7848129a387ff3c90ee1ebc26691d9a8  ./boot/grub/x86_64-efi/reboot.mod
e58cf6480f42b88d7c8c991365cc14f7  ./boot/grub/x86_64-efi/lsmmap.mod
5b0b5ccbde06a09bad681a4f6ea7c6e0  ./boot/grub/x86_64-efi/gzio.mod
ceaa71fb49eb2b8656579425f962bd7a  ./boot/grub/x86_64-efi/usbtest.mod
ee3ea066fdbc535fd28b21d1614cd71c  ./boot/grub/x86_64-efi/legacy_password_test.mod
16a620ffd3c91ab7e9c991c17b0aece7  ./boot/grub/x86_64-efi/bufio.mod
cb455d1967d9ed946d35ad7951e97424  ./boot/grub/x86_64-efi/udf.mod
70cf69962bf0f4402699dcfe20defd77  ./boot/grub/x86_64-efi/pbkdf2.mod
32abe8f90485646b5766fe0cd48a8dc9  ./boot/grub/x86_64-efi/video_cirrus.mod
7737422b5b0d147c3901c728ff886ef2  ./boot/grub/x86_64-efi/nativedisk.mod
2aeed8de15fdd3546978514b563ea42d  ./boot/grub/x86_64-efi/disk.mod
2dcdf59b7d50496c24571ab7219b89b2  ./boot/grub/x86_64-efi/cbfs.mod
80fcea92b1a80e5e9b3ec5fc3bf69a71  ./boot/grub/x86_64-efi/cmdline_cat_test.mod
d3af11e87c2ba4c5dd34be4dfdbb30f5  ./boot/grub/x86_64-efi/regexp.mod
8606bb03cbdc9edffd2bf9af69bbacf7  ./boot/grub/x86_64-efi/minix_be.mod
6603d2a5030d375858c08cfc7e8db4cd  ./boot/grub/x86_64-efi/priority_queue.mod
1eb37a27df3dcea08a0636f201dd7180  ./boot/grub/x86_64-efi/trig.mod
d4372a47fbe43dde36f59fca37d062f2  ./boot/grub/x86_64-efi/tga.mod
8535a5988b9bb74caccbcfb8d590dcb3  ./boot/grub/x86_64-efi/usbms.mod
0223822c7a6c768f5beb1686d430b7f7  ./boot/grub/x86_64-efi/terminal.mod
d6c4506b360ad2b1f32d998c2c52dc50  ./boot/grub/x86_64-efi/gcry_seed.mod
4f88232c0f700d0d781160e0030fea31  ./boot/grub/x86_64-efi/exfat.mod
96d08c2a687a4c034067fed0ad201345  ./boot/grub/x86_64-efi/serial.mod
3e5a9d783f25b8be69713f1bd5468ee3  ./boot/grub/x86_64-efi/probe.mod
7664b47d3b9c4e6bcb3ab657d48ce4a6  ./boot/grub/x86_64-efi/part_gpt.mod
1bb47874e7a7a1cdd79c22894fc03a00  ./boot/grub/efi.img
de0de72f71959f46a37cab971a88554d  ./boot/grub/grub.cfg
7f38fcdb9bc1d941fdcde3d832a97326  ./boot/grub/loopback.cfg
a28976a8bd8a9b2ec722556058cd7f01  ./boot/grub/font.pf2
c59c71b680907d9b0e74d9977d27d5fd  ./casper/filesystem.size
3801ce343809f5082beeadbaa75d29b5  ./casper/filesystem.manifest
0eac6346ce137e9befce6ceb9667228d  ./casper/filesystem.squashfs
8c51b6fbad7a4cd0c9756a129a6d058a  ./casper/initrd.lz
2902c6e94b680dc5a068543b716118ca  ./casper/vmlinuz.efi
5fae94d3a7ba9427f8b5a14315d3cf91  ./casper/filesystem.manifest-remove
d462db9c8932b1b4c53ada992de0263f  ./README.diskdefines
597bd61f5dc069694e425070241bd2d9  ./dists/trusty/restricted/binary-i386/Release
4a4dd3598707603b3f76a2378a4504aa  ./dists/trusty/restricted/binary-i386/Packages.gz
201f8af37ae22eb13dee92945108361a  ./dists/trusty/restricted/binary-amd64/Release
9e276f29a9e5eaf37e52c78f670289d2  ./dists/trusty/restricted/binary-amd64/Packages.gz
7a1a73021f44b59c0e209257b77b6c78  ./dists/trusty/Release
adbd3b6ffe4570ee8a601234b9dbed1a  ./dists/trusty/Release.gpg
60cd95dff4f53976b4179a8a061a666e  ./dists/trusty/main/binary-i386/Release
4a4dd3598707603b3f76a2378a4504aa  ./dists/trusty/main/binary-i386/Packages.gz
52d605b4217be64f461751f233dd9a8f  ./dists/trusty/main/binary-amd64/Release
2cd5bd7a1a401bf5f456592581d9e361  ./dists/trusty/main/binary-amd64/Packages.gz
2dea446027fde0b8623db959ff8723fb  ./install/mt86plus
```

---

### Post by QIII on 2014-09-05
The low-down on checking md5sums is [here]("https://help.ubuntu.com/community/HowToMD5SUM").

However, don't use the hash page as suggested.  It is sometimes a step behind the times.

Go back to the official downloads page and get the hash from there to check.

Cheers!

---

