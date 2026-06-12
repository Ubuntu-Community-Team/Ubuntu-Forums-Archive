---
title: "Can't install Ubuntu from CD"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by gwoodard on 2007-02-25
I burned an Ubuntu 6.10 iso image to a cd and i tried to install it on to another computer, since the cd didn't go first and it booted to the hard drive. Here is the boot order as follows

Atapi CD-ROM
Hard Drive
Removable Drive (Floppy)
Disabled

My current config is

Windows Me
Intel Pentium 3 1 ghz
Compaq NetIntelligent Nic
Onboard Video
Onboard Sound
512 mb PC 133
6.4 GB HD

I tried to install Ubuntu from My Computer -> CDRom (D) but all it came up with was to find a program to install from besides the cd

---

### Post by Stemp on 2007-02-25
If your boot order is cdrom first, I guess your cd was not burned properly.
Did you burn an iso image ? not writing the .iso ?

---

### Post by gwoodard on 2007-02-25
Yea I did... I burned an iso image on CDBurnerXP Pro on Windows XP

12x speed, did I need to burn it slower?

---

### Post by Stemp on 2007-02-25
> 12x speed, did I need to burn it slower?

Maybe, but I don't think so. If the cd was corrupted it should start anyway but with an error.
Anyway try to burn it on a slower pace.

---

### Post by gwoodard on 2007-02-25
Thanks, I'll try it at 1x speed

---

### Post by gwoodard on 2007-02-25
Tried and failed... I tried Winace and  I still can't get it to install

---

### Post by Stemp on 2007-02-25
Winace ? don't know what it is.

Do you have another boot cd ? like win xp. Is it working ?

---

### Post by gwoodard on 2007-02-25
Yea... Why?

---

### Post by Stemp on 2007-02-25
Why ? Because or your Ubuntu cd is corrupted or your bios setup is wrong ;)
BTW did you check the md5sum of your iso ?

---

### Post by gwoodard on 2007-02-25
Yea, all I got was this 3d0310e32d0b174a312ed2c1f7ec022b  ./dists/edgy/main/binary-i386/Release
e98d92672ffd1ed2a26199ef7b8b66e5  ./dists/edgy/main/binary-i386/Packages
c577fd0592de8ddc7d33454cf9ac3482  ./dists/edgy/main/binary-i386/Packages.gz
a2227679f488421d96e453379fa75e82  ./dists/edgy/main/dist-upgrader/binary-all/edgy.tar.gz
7709cced6f6cd8d3cb54e595f0fac24c  ./dists/edgy/main/dist-upgrader/binary-all/edgy.tar.gz.gpg
4aefa006e7c7cdc88d6103608d2fccdc  ./dists/edgy/restricted/binary-i386/Release
c0322f97ca811198cdc523c9c7334a70  ./dists/edgy/restricted/binary-i386/Packages
2410f8c0cb77315ac395c57c8b87c238  ./dists/edgy/restricted/binary-i386/Packages.gz
b8cdf91ed622872ec45cd5040cd5408a  ./dists/edgy/Release
1cc6b9f403aee712ee449119377f246d  ./dists/edgy/Release.gpg
ccbc5a8d93b10590193084e179fe4492  ./.disk/info
3d37f215b76490b1ad5bd94607c7e292  ./README.diskdefines
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm
1473ccac5ddaad89c2b8dfefcc5770de  ./install/mt86plus
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
23d9bfe897b4264f2465e8a592ebb6e3  ./preseed/ubuntu.seed
065e8df1eba53019a42df404f20765e2  ./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.17.10_i386.deb
88419877278c99a0fe382dbd95b89c7f  ./pool/restricted/l/linux-restricted-modules-2.6.17/avm-fritz-firmware-2.6.17-10_3.11+2.6.17.5-11_i386.deb
a69b413b3f00e33190f9370facb51eb0  ./pool/restricted/d/drdsl/drdsl_1.2.0-1_i386.deb
36804460fdf62473f56850aaf3c374da  ./pool/main/b/bpalogin/bpalogin_2.0.2-9ubuntu1_i386.deb
9555bbff826c8f059d00a824d6285275  ./pool/main/b/build-essential/build-essential_11.3_i386.deb
e131a82ca44c7092e2ec8a5f42edaaa3  ./pool/main/i/isdnutils/capiutils_3.9.20060704-1_i386.deb
7fc022c924c021f5dc11853287438166  ./pool/main/i/isdnutils/ipppd_3.9.20060704-1_i386.deb
0b56331a35ebf44217470406a4a390c9  ./pool/main/i/isdnutils/isdnutils-base_3.9.20060704-1_i386.deb
aa4518f5543c7b5de729eb0db33cacbd  ./pool/main/i/isdnutils/isdnutils-xtools_3.9.20060704-1_i386.deb
e7475bb90c65e69fe10d132b522b050c  ./pool/main/i/isdnutils/libcapi20-3_3.9.20060704-1_i386.deb
33b1179fc56274c820f6cdd5f9757f73  ./pool/main/i/isdnutils/libcapi20-dev_3.9.20060704-1_i386.deb
b3238462a2c99c0ec7b5ee8a5b3f2462  ./pool/main/i/isdnutils/pppdcapiplugin_3.9.20060704-1_i386.deb
08b5e52a9543b70569d4465adbbf4ac3  ./pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb
e0a52d89b979e2f8602ef9cdd0e6f0b4  ./pool/main/e/eagle-usb/eagle-usb-data_2.1.1-2ubuntu1_all.deb
6f9b0c0cb03ef24dd0534e00440e5551  ./pool/main/e/eagle-usb/eagle-usb-utils_2.1.1-2ubuntu1_i386.deb
7f9edbbfaa0131664bb76921c510c4ef  ./pool/main/f/fakeroot/fakeroot_1.5.9ubuntu1_i386.deb
0a51efffa556cd06f07557bf78f1aa28  ./pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_i386.deb
e6e00d68edc0daae2572ad53663fa9a9  ./pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_i386.deb
bfd9a8deeb07f495bf75bfb9d83fdebb  ./pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb
cb79022ae226507d1f86af9c5421f667  ./pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb
245f16de0196793b159380d0f9182334  ./pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb
77f805ee8b0099629f1f5311d63578b3  ./pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17-10.33_i386.deb
a396df2a8abd6b430b47f9f2cd23c01e  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.5-2ubuntu1_i386.deb
3d9fe86fb30086a4eba9aec6a4f06ef7  ./pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb
6ba955830847e6e20282291ff124b34d  ./pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb
7e111f78aba5d2a4ce5880535160ce03  ./pool/main/n/ndiswrapper-1.1/ndiswrapper-utils_1.1-5_all.deb
0f4e21e2ca0560558355909b2f7f0e03  ./pool/main/n/ndiswrapper-1.1/ndiswrapper-utils-1.1_1.1-5_i386.deb
e0455774d32284b18d0af7812cd16a3b  ./pool/main/p/pptp-linux/pptp-linux_1.7.0-2ubuntu1_i386.deb
e9c14f4a5a1a7f930d676d335b326fb0  ./pool/main/s/setserial/setserial_2.17-43_i386.deb
bc0922e243eef7f11d3bc58faa4003a7  ./casper/filesystem.squashfs
cc8fe91fe96b5f693e928f9865d0ae1d  ./casper/initrd.gz
0a15562c9c16e5d2b35a83816a894667  ./casper/filesystem.manifest
10935d6293597ad99866d2ff16591477  ./casper/filesystem.manifest-desktop
d595c0f38ff1e91efdc871b93a6fe20e  ./casper/vmlinuz
85aa3dc1dd5e04077d7a34cb1d37d02c  ./autorun.inf
3439d43574651fa57fcd8d8dbc303983  ./start.bmp
d5af1fcc69d14bf1f340e31108121415  ./start.exe
ab80ef2060c666906fc06acc29735bec  ./start.ini
59847bb83384524a9c3ab577b23f8f69  ./ubuntu.ico
490e29716ff3ff0323589fbdb79e00c2  ./programs/thunderbird/ThunderbirdSetup.exe
1a190a15ba452a28025d28f780db648e  ./programs/gtk/GTKSetup.exe
c26a6087491045f62402fd182bdf4794  ./programs/gimp/GimpSetup.exe
0905a05e0653e3899e2f54fe5f5dbc8e  ./programs/gaim/GaimSetup.exe
34cbc9f8ad5d41ad37ab8bea24cb688c  ./programs/firefox/FirefoxSetup.exe
120622531f51091f5b1e2a619782501e  ./programs/abiword/AbiwordSetup.exe
390e4ace8948b303ffdba01daa8b275e  ./disctree/incl/js/ocd_common.js
153de8cc94538885d7fd6fed45a24a05  ./disctree/incl/img/backarrow.png
8fda0f36418c2639ead2fe03a114463b  ./disctree/incl/img/gtk-big.png
6e6e1399ff211d0e23fd5d37119fe2e9  ./disctree/incl/img/gtk.png
55aaa568e345e79a20d89459bb4aea3e  ./disctree/incl/img/opencd.png
55ecbf80d6d870994a89ba21d01ef817  ./disctree/incl/img/shadow200.png
a9d6ded28f002c874e0fb79fa8949e5f  ./disctree/incl/img/info-i.png
e9e6cbca18dc255efebaede8e5c6a20e  ./disctree/incl/img/install-s.png
021c1df7848c4f3ba0be4d4936ba79af  ./disctree/incl/img/gohome.png
64df0b4395a290af84e19ab0385cb065  ./disctree/incl/img/install.png
f8fa67e5952cef3c9c28f87cc6ec4b29  ./disctree/incl/img/ubuntu-logo-small.png
ae98d3d89e724abc86b2688bf8ab69ca  ./disctree/incl/img/ubuntu-logo-large.png
9765b4a462e87f31f7367c46e36e665e  ./disctree/incl/img/globe-s.png
8a20b1d99c11f24b2d80060b7814b003  ./disctree/incl/img/white.png
07ff0fb9f7a311affb490257586bb273  ./disctree/incl/img/ubuntu.png
c03b3503d1a2bcdc710876fb0e3a7daf  ./disctree/incl/img/thunderbird.png
54bdf6d56535ded07472f8eca2ede5c2  ./disctree/incl/img/top_amber.png
d83ce908fddc90693c3a31244d0756ac  ./disctree/incl/img/shadow250b.png
0b71f01abbdbebba264717249ba97cfb  ./disctree/incl/img/shadow250.png
a70f09fc33a8ffbdbeb9de789d3e8587  ./disctree/incl/img/shadow225.png
794941b3f1617f833b9a8e1c0b8aaddb  ./disctree/incl/img/gimp.png
bd48326516c0ca19047a0686db807353  ./disctree/incl/img/gaim.png
b2727f0512fa13b50c9dba997b734fc7  ./disctree/incl/img/firefox.png
b0ea5c71f4e202d3fa0c9b2c84ae621f  ./disctree/incl/img/exit.png
95d374744a18b572f3aa4905a390df9e  ./disctree/incl/img/bullet.png
acf1c2de86a6f0d4105d58c2ed2d5670  ./disctree/incl/img/body_btm.png
b7ab52b2fa3fc0bab74cc1d352c0ca85  ./disctree/incl/img/bkg.jpg
a9a4e7d38a483562ef1aead402b9e8ef  ./disctree/incl/img/abiword.png
bd05b08bdd7197f3082fed8f5f6717cb  ./disctree/incl/css/info_page.css
80a02f7a6e6cdfee5abe2fb88950e453  ./disctree/incl/css/main_page.css
40b14bca2dacc2216aa6438af049f806  ./disctree/incl/css/common.css
0a55e77d3cf09f0f58d07ec772e54c2d  ./disctree/incl/css/app_page.css
4d39c767ef07bc683a40e38feb96ad56  ./disctree/incl/source_web.lch
1e82859532a2dedfd65633d503cca630  ./disctree/incl/orchard_web.lch
eb4a5070e668e9b7699b02df2167d888  ./disctree/incl/kmeleon_web.lch
b6319939c3e3d3b3f63c2bef0cec18ab  ./disctree/incl/InfoWindow.html
731cddbcdda9d8656e481f64df5c822e  ./disctree/incl/forum_web.lch
080b221ce67aef686fa39f39de933da4  ./disctree/en/gtk_web.lch
4797a06db6c4db4ae3d7080b10b534bc  ./disctree/en/gimp_install.lch
1ac7301f7c8cab7e701dbcae34926cd0  ./disctree/en/gimp_web.lch
8bf2506ff7bfcf2c937f14af215bff90  ./disctree/en/abiword_web.lch
0725ea8be010775eb8bc739876a5b53c  ./disctree/en/thunderbird_web.lch
74d40304d5e9d745bee905f95cd9c100  ./disctree/en/gtk_install.lch
cd2f64979933cdaefd99940b830fd204  ./disctree/en/aboutgtk.html
37b86a5c510907b44e7f040fa180dd5c  ./disctree/en/abiword_install.lch
e8327b1c66fd2275160eef0d941019ab  ./disctree/en/thunderbird_install.lch
e797bfcf73470f7c6d5bd435b5f805c1  ./disctree/en/gaim.html
d160610f5a209024d91daba53fb90a23  ./disctree/en/gimp.html
7f63ce8f441c3f020c01f2ac424753ee  ./disctree/en/firefox.html
25eeaab2c0624a1e24642551969d3768  ./disctree/en/abiword.html
1af0dda63a79d1db63c09bceebe71889  ./disctree/en/home.html
4291651a1d4353442ad0a6336f831d33  ./disctree/en/ubuntu_web.lch
3fb49ab17ccb5135f8842c3d22bfc28f  ./disctree/en/thunderbird.html
ea82579c3e3a7a115ea678c686288a59  ./disctree/en/theopencd_web.lch
080685dd7456eedc79c25fdb364bcb5a  ./disctree/en/opencd.html
1301cf7d2c890451c8bb6fd13bc970db  ./disctree/en/gaim_web.lch
7c253943d92b9cdef7bbe688de3d9caa  ./disctree/en/gaim_install.lch
908fafb3125239d0504531e96acfde55  ./disctree/en/opencd_web.lch
18b5a6deb5198c3856480901517e30cb  ./disctree/en/firefox_web.lch
6f763dfde10ae2f68bc9061c8572bd81  ./disctree/en/firefox_install.lch
1515c78debceb3e7b9ac0d00bd95b750  ./disctree/en/ubuntu.html
49cea37bea2547e6e3301814229a4bc6  ./disctree/app_img/ubuntu-nautilus_tn.png
54dc901081f1b9e000e28cbb03c7ad9d  ./disctree/app_img/ubuntu-addapp_tn.png
00e18b0dc90f1dc2eb600d66c0862481  ./disctree/app_img/ubuntu-addapp.png
d0764600ab07ca54d21c1d880c0d6405  ./disctree/app_img/ubuntu_225.png
908f46330bf9910732b59ca00a60aa0a  ./disctree/app_img/ubuntu-desktop.png
8f711d69ac36b1d6cbec438c93c25e3a  ./disctree/app_img/ubuntu-nautilus.png
d3e5d5703ff042e7881e5bf86d734609  ./disctree/app_img/ubuntu-gimp_tn.png
0f91afaff02cf9f25913d8b4bd342c89  ./disctree/app_img/ubuntu-gimp.png
8987a5bc9a149a9f6fc095133c6349fb  ./disctree/app_img/ubuntu-desktop_tn.png
fe2deee305807e3a5728364ccfddd5fc  ./disctree/app_img/gaim_01.png
bea27276328ccf4ec42411ac55f0e6fb  ./disctree/app_img/firefox_02.png
9843b365c4111c1ccd653e1d2376e0fb  ./disctree/app_img/firefox_01.png
aca756da80f8bc43311d55c4bd3d9ed2  ./disctree/app_img/abiword_02.png
882f731bb225dc88ec98444025ed5eb6  ./disctree/app_img/abiword_01.png
cc2f5cf1e74a2d3d7c0dc0728c906c3d  ./disctree/app_img/thunderbird_02.png
36c2e81633eee5cb9580ca4fe9260359  ./disctree/app_img/thunderbird_01.png
cee0cfe6690e866741fd86bc57d80b34  ./disctree/app_img/opencd_02.png
7f61f54479a23a172043778c9e0f04a0  ./disctree/app_img/opencd_01.png
c6a89be98be6d801bd90d58336adebf4  ./disctree/app_img/gimp_02.png
5a3c889428defab7d91c79a94f256792  ./disctree/app_img/gimp_01.png
106e0b054e1ef94984d417f765907f38  ./disctree/app_img/opencd_01_tn.png
2abdff5d8f72820882068b23e3d739d5  ./disctree/app_img/opencd_02_tn.png
8ba41a6676658ff6d6836b066d5cc88a  ./disctree/app_img/gaim_01_tn.png
551b660d8cc2078a0121a3d9bb27041d  ./disctree/app_img/firefox_02_tn.png
207f629183d73ddc968fea8411f2014b  ./disctree/app_img/firefox_01_tn.png
2bb851acf5c12bb111f8894d0fad0b72  ./disctree/app_img/thunderbird_02_tn.png
eb806361ed1de84afc2f75029b42c9a3  ./disctree/app_img/thunderbird_01_tn.png
0cf8ce4bfddd0f214d69e2ca3ff8a999  ./disctree/app_img/gimp_02_tn.png
434f303e5a8f5ce676d9be5dfe82e31a  ./disctree/app_img/gimp_01_tn.png
00a2d477f914645095a090dee561b872  ./disctree/app_img/abiword_02_tn.png
0b1deee3753102a4d53b3e36ccaad8f5  ./disctree/app_img/abiword_01_tn.png
471f7aaef12fa84ec56afbf28c44ba05  ./bin/res/html/gopher-unknown.gif
ca091587f135c792890a714df83f7464  ./bin/res/html/gopher-text.gif
152f38b3bdfa36be6e424d6870fb7687  ./bin/res/html/gopher-telnet.gif
0c428f6883c912e150ce42c954b1bd36  ./bin/res/html/gopher-sound.gif
fb4779eea87a41f19e0fb21fd8718779  ./bin/res/html/gopher-movie.gif
7c2f66288e1c62c766b6b68878a4fd4a  ./bin/res/html/gopher-menu.gif
2734f280b5cc8219706db1bda4564cbb  ./bin/res/html/gopher-image.gif
2f847301ecc366bd4c24c93057be436d  ./bin/res/html/gopher-find.gif
7544430afba18e7d21927bcfe6337378  ./bin/res/html/gopher-binary.gif
0c428f6883c912e150ce42c954b1bd36  ./bin/res/html/gopher-audio.gif
f671c95b3ff839591e2402768ad8f43a  ./bin/res/fonts/mathfontSymbol.properties
24121428d430c35793178ea59f560e41  ./bin/res/fonts/mathfontPUA.properties
5e9b13e2fc2dbaaea0076971e27f03bf  ./bin/res/fonts/mathfontMTExtra.properties
abe2e04db7a51e39819aa7d00875e125  ./bin/res/fonts/mathfontMath4.properties
1cbe639d9a0b98a29518ae188147824a  ./bin/res/fonts/mathfontMath2.properties
1332997587e5a240fcc3f73c6632c024  ./bin/res/fonts/mathfontMath1.properties
570c55e3a5599139ab29983d96483151  ./bin/res/fonts/mathfontCMSY10.properties
20104544c58bfbdf705cd3b6e01e46cf  ./bin/res/fonts/mathfontCMEX10.properties
32c76794b8405032a0ca4a6cdb1b025e  ./bin/res/fonts/mathfont.properties
a3804f3d1dfcda0dce652382f99956d9  ./bin/res/fonts/fontEncoding.properties
751720cf07297a3e704c46870af5dbe5  ./bin/res/entityTables/transliterate.properties
69328a3f978e27edf755a5a81332de3f  ./bin/res/entityTables/mathml20.properties
08ae7554b418ce296529350cf08b12a9  ./bin/res/entityTables/htmlEntityVersions.properties
bde618ca804a398732e761dbc1e42573  ./bin/res/entityTables/html40Symbols.properties
1debc398d874fa3bc47a7abfe1c39760  ./bin/res/entityTables/html40Special.properties
8e39cc35db69989a275d946b2fccf70f  ./bin/res/entityTables/html40Latin1.properties
e0f5416f4ed6e8b94769c3ddd6f1c516  ./bin/res/dtd/xhtml11.dtd
8299e5629c0e5b0d3259047e68723748  ./bin/res/dtd/mathml.dtd
df5e84f613c8549777e3f7e4c821c3d9  ./bin/res/builtin/platformHTMLBindings.xml
8429106cb073d5b4302ddd3f02af039d  ./bin/res/builtin/htmlBindings.xml
fd8591fd84315a4d7e77ba2b3afa16ae  ./bin/res/wincharset.properties
76d6deb8106b97e0f392413e0e674c9b  ./bin/res/viewsource.css
f834a04923745b4c78561682f78f991f  ./bin/res/ua.css
07cb5f31792b5f4c83f017b06ec74ddb  ./bin/res/quirk.css
ff74605f7c3948949359d81e4eb4535b  ./bin/res/platform-forms.css
dd758806a8ab7b8523ee79aab7301f9c  ./bin/res/mathml.css
e41b2867558df65d6a42a0b53a7c2faf  ./bin/res/loading-image.gif
7825365e7edd86fde753f20b821e30cb  ./bin/res/language.properties
bf3417a5fe5f311a693a37aa904beb05  ./bin/res/langGroups.properties
f6c6e078d7d23aac4ba6151d197a28e7  ./bin/res/html.css
ccf39b06aa3282d0a1f9e7582418583d  ./bin/res/grabber.gif
73a30aad4693466fa5c3588ce7e4e226  ./bin/res/forms.css
39a4bc82773526a359c1bbebb159b063  ./bin/res/EditorOverride.css
ac8a0ff756ef0956622fadc94946e7da  ./bin/res/cmessage.txt
2f941035c3993a5ba36b1c8a7d90efe8  ./bin/res/charsetData.properties
c08872b47860f13030203bd600a1eec6  ./bin/res/charsetalias.properties
1f689efbc0c154a9f812f033d6cfb327  ./bin/res/broken-image.gif
9d562b1fca17886ff56c0dcc71159a0c  ./bin/res/arrowd.gif
c72551f52990bbec40e4b0c2dfad4812  ./bin/res/arrow.gif
c50d0bce0158737ffbee24dc7d9b9041  ./bin/plugins/npnul32.dll
5dd4f967decc41c6accda743a7add54c  ./bin/kplugins/macros.dll
88df037a0770a9fc1d51a9ad1ac0fd43  ./bin/ipc/modules/transmgr.dll
e157e37854f31c71b22b41d7d6787d35  ./bin/ipc/modules/lockmodule.dll
d2b52083c3bd14f8edc59b2c4d3b1f8d  ./bin/greprefs/xpinstall.js
287bd26fd55d1db28493aef31f17161d  ./bin/greprefs/security-prefs.js
c3b3c17378033aafd8ecc4afed42e2fd  ./bin/greprefs/non-shared.txt
f02237fe27eb39cf5d319bcd0ebc2ef3  ./bin/greprefs/all.js
0741073fe5429e3544191a7deef4fb26  ./bin/defaults/wallet/VcardSchema.tbl
b04032e5f725dbc0d455de93d78e6790  ./bin/defaults/wallet/StateSchema.tbl
e057e75e8061a238f4d818790401e4dc  ./bin/defaults/wallet/SchemaStrings.tbl
7aaabe59916552a34b2b7307af8834c4  ./bin/defaults/wallet/SchemaConcat.tbl
6c028265e688b5e88ac5860bf2cb61db  ./bin/defaults/wallet/PositionalSchema.tbl
79fa80c9cb6d8ee2922e795b7d131d84  ./bin/defaults/wallet/FieldSchema.tbl
332b1f2ccbb75bd3540de695bfc34bfc  ./bin/defaults/wallet/DistinguishedSchema.tbl
2fb4983a725f789182ab67eb3fd3cf25  ./bin/defaults/profile/chrome/userContent.css
d41d8cd98f00b204e9800998ecf8427e  ./bin/defaults/profile/chrome/userChrome.css
4193470912a8f8064a1d2a6f7e624229  ./bin/defaults/profile/user.js
713424d5bfcf7a48488071ef35c59427  ./bin/defaults/profile/Prefs.js
55ac2c00c523abccb3a66c89dea315d9  ./bin/defaults/profile/mimeTypes.rdf
3324094de3946ab0703f19f700b81ed7  ./bin/defaults/profile/menus.cfg
76e531a9c951335d63cdb52920b2f4b9  ./bin/defaults/profile/macros.cfg
1dffd2301292331f10c1e23a9e0a878c  ./bin/defaults/profile/localstore.rdf
d41d8cd98f00b204e9800998ecf8427e  ./bin/defaults/profile/history.txt
2c3192e97e909eec87090324a85e6062  ./bin/defaults/profile/cookperm.txt
2ffaea0a9579122a995e0f4bb354bd86  ./bin/defaults/profile/cookies.txt
df1863462fc67dcca113cca8b0f35ac2  ./bin/defaults/profile/accel.cfg
5790efd2536112bad3114b170f454ace  ./bin/defaults/pref/winpref.js
fbb56166b6a2e58d7ef1c4d8d20c4937  ./bin/defaults/pref/security-prefs.js
ea01a6d5d5428f3926b0722aa263d5d6  ./bin/defaults/pref/all.js
2bf214f9c956736c2e7e0ed709073c17  ./bin/defaults/autoconfig/prefcalls.js
07cd65785a8104bfd3cca17e039d3d7a  ./bin/defaults/autoconfig/platform.js
08079125b89db96f237ba8dda98e36b9  ./bin/components/xuldoc.xpt
342eaa862126fb8f060c3dbb2e3ef2bb  ./bin/components/xppref32.dll
355b3ea8834c28407bd0711e4c078392  ./bin/components/xpconnect.xpt
ff1774deab1d1510ca8a1bb73aedca57  ./bin/components/xpcom_xpti.xpt
3f35e0e7d9b38ccad07e2af43b9d4361  ./bin/components/xpcom_thread.xpt
040d028807cbf63af1a568dd90e1022b  ./bin/components/xpcom_obsolete.xpt
234b9b3850df0103945e3f2ae8f8079a  ./bin/components/xpcom_io.xpt
1b71738dfce69f8097bcab8aae41bde9  ./bin/components/xpcom_ds.xpt
205bf5918ae37dd0b277d2e162cfe2dd  ./bin/components/xpcom_components.xpt
2125a04ee426ca4feec855ec8c2e95b2  ./bin/components/xpcom_compat_c.dll
c80abb2cca02dc2f45925c47e0a0bff3  ./bin/components/xpcom_base.xpt
3faa49357d44badec4ccebc0794e56b9  ./bin/components/xpc3250.dll
2689a7bb39316f80a7ff6d22cebd72c6  ./bin/components/xmlextras.xpt
96a9bb517ab132b85c21e5348890a238  ./bin/components/xmlextras.dll
c8be7e60f6d2f34342d95ba4c8a99a53  ./bin/components/windowwatcher.xpt
f72dee0a0fe606249cfa176c708d4966  ./bin/components/widget.xpt
f810819f8213c70d163b7df8265efe97  ./bin/components/webbrwsr.dll
5321057d7ca47f9e28be5a6a5867e975  ./bin/components/webBrowser_core.xpt
fd0e57ca2d9239abfdcf69dd983c83e4  ./bin/components/walletpreview.xpt
f3542d24c9c849b34ee41255129449ff  ./bin/components/walleteditor.xpt
cbd41f95c1c563461c1e0083e8ad0aed  ./bin/components/wallet.xpt
e3878705f1cf6aec390c4271d0a74ce4  ./bin/components/wallet.dll
408c82221dc50b914fcb0929479ee7a1  ./bin/components/uriloader.xpt
4c45b5f44dbdb6ee67dcac3127350886  ./bin/components/universalchardet.dll
e83312c13bf50738ce4dbf024670d72f  ./bin/components/unicharutil.xpt
748b771357ea094ede248c9a6041698c  ./bin/components/ucvmath.dll
7cd43b1d5dddfdc455f736e87c926345  ./bin/components/uconv.xpt
414ea5cbe3d23bb5b6d832c8a32664b9  ./bin/components/uconv.dll
6fd588161af39f7c615ce817b1511b16  ./bin/components/typeaheadfind.xpt
1de96ee53e95491b5e76fa5ab23b9db1  ./bin/components/typeaheadfind.dll
11000ff719bd6ead71631c62cab4e6a9  ./bin/components/txtsvc.xpt
d9897a726e6745dbb61daca142153b6a  ./bin/components/txmgr.xpt
185a0993abb5bf56ea8ec2971f2a6ed3  ./bin/components/txmgr.dll
e2d305fec292fd23e26762057fc34829  ./bin/components/sidebar.xpt
7dade93b05ed22c350815f84162b05ee  ./bin/components/shistory.xpt
2cdb9a40246eb4415f420e6c0f039c90  ./bin/components/rdf.xpt
a9f31c342bfb41c92463c42c11243e52  ./bin/components/rdf.dll
2c958b04e79fb1df3ae058a28fefe3dd  ./bin/components/profile.xpt
f0faa6068e76f2bec3aa7c4d3b9741ee  ./bin/components/profile.dll
6e2021ec48b65af50774616e20686855  ./bin/components/pref.xpt
7b220712e4f5884efd54eb6749a92a06  ./bin/components/pippki.xpt
a709ecc625c74ccd57e7431a972d21d0  ./bin/components/pippki.dll
f521c4aae559eabeff39a892a618bfb1  ./bin/components/pipnss.xpt
f8f9b228fe6cc33681f72f9394a361d4  ./bin/components/pipboot.xpt
5cfad92e6804ba33aa03f1b36b274061  ./bin/components/pipboot.dll
ebea0299d8ea2c9e1dd3f4c38b285f33  ./bin/components/p3p.xpt
bce9185e0801a5a5090ddbac26a6b8f1  ./bin/components/p3p.dll
7d1e46e3c6170de0219997870068be44  ./bin/components/oji.xpt
6ee2b03016a59cb9ea90f94617931021  ./bin/components/oji.dll
9a2450959092a9ffb546f17eb6005329  ./bin/components/nsSidebar.js
578fbec8b5aaa9ac0b33957aeebee44c  ./bin/components/nsProxyAutoConfig.js
619d71feb1eefcc26d9b04d08124855c  ./bin/components/necko2.dll
acbea5b9b887a9cdac4faa2e2c361ffe  ./bin/components/necko_viewsource.xpt
5ad3462450b3102cb9f7386d7a6da081  ./bin/components/necko_strconv.xpt
b4fa7b5c6e19bded5ee08b1c28de0b64  ./bin/components/necko_res.xpt
ad3d229c303b8596fd0da33664576961  ./bin/components/necko_jar.xpt
4a2c5cbe583c7d591f895cae4c189c65  ./bin/components/necko_http.xpt
d8a07beb05e97c62ff25b6d54e83267a  ./bin/components/necko_ftp.xpt
84a5f8aa6f0abebffb1e4daf875639f4  ./bin/components/necko_file.xpt
7694540a8f37f218df21bbc4db4b1273  ./bin/components/necko_dns.xpt
6233b02d077a9788dc96b6e91e20ca28  ./bin/components/necko_data.xpt
2c159f91ddd21e32c9362df29accc595  ./bin/components/necko_cookie.xpt
258af59879f22c3b73968c17f3f14c97  ./bin/components/necko_cache.xpt
ef1d011a911bb53be028284f3005e146  ./bin/components/necko_about.xpt
359d4fd13883958840d5f45afb017e1f  ./bin/components/necko.xpt
660862a3504908e2b17a88aaadd7590f  ./bin/components/necko.dll
2b0209249378ac66fa64be9496ea5e0b  ./bin/components/locale.xpt
2a4513024d887325ee0571eb40f0c50d  ./bin/components/layout_xul_tree.xpt
2f13c12570ea90a0711bd5cd8b1a877c  ./bin/components/layout_xul.xpt
6a8ad6ed90dd4729863de82d5b0281c8  ./bin/components/layout_base.xpt
fce20e3e7d15e1413e37f04b9cd5221b  ./bin/components/jsurl.xpt
f6cf760fb9a21a228ea79af9c9078ef3  ./bin/components/jsdservice.xpt
55040a86baa32d024b1734e8feeae9ef  ./bin/components/jsd3250.dll
ef5a351e35da4091b5ee6285ae7e74f4  ./bin/components/jsconsole.xpt
a8dbcd0d4ba174b3b536d6b73492eef1  ./bin/components/jsconsole-clhandler.js
9e75f553350c270ea084beae9ca3cc4f  ./bin/components/jar50.dll
d723fbae52c7601f60633a8fcd5ff939  ./bin/components/jar.xpt
f8794ee8fe082984dc80078e544f8993  ./bin/components/ipcdc.dll
e1dc5c602986243bf878bc35061003d1  ./bin/components/ipcd.xpt
c0511ee58a85b9351c941475536ba7a2  ./bin/components/intlcmpt.xpt
069ebd97cebaaafa10e5a0ee5c91abaf  ./bin/components/intlcmpt.dll
29cbe89849233b59bdb14d68a37d39d8  ./bin/components/intl.xpt
1bbddb99f2400103f0dc32c9a6f50008  ./bin/components/imglib2.xpt
9531d0019e2bcb760183a7917beaa5d6  ./bin/components/imglib2.dll
9bf06995a360cb583df91e72deaa5f1b  ./bin/components/i18n.dll
97beb6ecc7609a16e5c77fadb4669828  ./bin/components/gkwidget.dll
92a5c5445f6de89384ec4c6b5b048338  ./bin/components/gkparser.dll
70c35ffa3c506f1a59d2fd3636ce751f  ./bin/components/gklayout.dll
5456d5274c8402088e931f71649fedd2  ./bin/components/gkgfxwin.dll
dceca5119a3a91a5f600b4d21e14c41a  ./bin/components/gfx.xpt
eca3fbb6237b67a55dad7df159f5b096  ./bin/components/embedcomponents.dll
e7cdace56627f44899da4a9f72a9096b  ./bin/components/embed_lite.dll
6a0e276e5b9a362b36e781761b4e999d  ./bin/components/embed_base.xpt
50ad6f6334b121ef99f0da2f6788326a  ./bin/components/editor.xpt
0c27999f59badbd59f4bc3e981b8e8f4  ./bin/components/dom_xul.xpt
bdf15c18d9e4feba4ba9714146a8881e  ./bin/components/dom_xpath.xpt
590eb5f7fee2b3831db3be4d1d9a71dc  ./bin/components/dom_xbl.xpt
f7f0f182acc7bd6295badb8121e1bd8b  ./bin/components/dom_views.xpt
5a91bebe5e413341a9b274232a85098a  ./bin/components/dom_traversal.xpt
c14e1dfc848fba5a05b39e7ba7814b3b  ./bin/components/dom_stylesheets.xpt
0f54e808bea39c5f542dbc72b646267e  ./bin/components/dom_range.xpt
4ebdf80f747378cdc88b1dc69edcc014  ./bin/components/dom_html.xpt
e184678d8fbea198ddf100abf174da12  ./bin/components/dom_events.xpt
3037eb540688399e8e31d2c15d3369a2  ./bin/components/dom_css.xpt
49eba6bfbe0976f2dc1f8d79fe17f7d2  ./bin/components/dom_core.xpt
261cfc577c768d7c48953e47b5a2ec54  ./bin/components/dom_base.xpt
64c664dae6428ca845f96a21a5a07c62  ./bin/components/dom.xpt
4d176ee8cb77b8a9415bea9fc65cedb4  ./bin/components/docshell_base.xpt
0d8a1978a9f624eb355b43dadd08cd47  ./bin/components/docshell.dll
471be0eb8136304f0c9c55c1655a2952  ./bin/components/cookie.xpt
bc8bb0d2031261f0e57748e353a10ead  ./bin/components/cookie.dll
1b674aa204ccd540e723682f8d2dda5c  ./bin/components/content_base.xpt
55169154065f1c31492533ea7608843c  ./bin/components/compreg.dat
49b8892f425494461702671433681b1d  ./bin/components/composer.xpt
3aeeb92c592a0381228065fa5bc23b82  ./bin/components/composer.dll
ba80b6445d3ddf907081353e7e25337d  ./bin/components/chrome.dll
76ffec7829d04bdc01f502353dd7ea81  ./bin/components/chardet.xpt
5b16e699fb3166ad02e5dad225313969  ./bin/components/caps.xpt
0e01a019423dad5bce26474a818a91d7  ./bin/components/caps.dll
c58f02d1a30d4103f4c47f9c067bec92  ./bin/components/appshell.xpt
d34e6d186c7fa5266584dbc84e232e48  ./bin/components/appshell.dll
7246595e3d99e36c94642c6c47a9609c  ./bin/components/accessibility.xpt
f4ce7ad3ea212a54cae35c4529d929d3  ./bin/components/accessibility-msaa.xpt
0ce55d3dc0246765632b8bea785d593f  ./bin/components/xpti.dat
5361a5008fe0806bd44ff559345dac0e  ./bin/chrome/overlayinfo/navigator/content/overlays.rdf
b5e79de3ce0d070a6e627bc618ad6f83  ./bin/chrome/overlayinfo/messenger/content/overlays.rdf
0bed9d09bda8fcdb5b3fc87a8379878f  ./bin/chrome/overlayinfo/communicator/content/overlays.rdf
2319353c89357c10a41f973a173f723f  ./bin/chrome/overlayinfo/browser/content/overlays.rdf
10fa2ae1c8f9a6805fa6e9ce72653137  ./bin/chrome/aggreg8/content/rssfeeds.rdf
d00a7d309fc9023536b70c1d3bedc011  ./bin/chrome/us.jar
b02ed46496f52acfceb3afc754024c53  ./bin/chrome/toolkit.jar
2f4a47e16b73e2bc41ba51e85fcb2f1c  ./bin/chrome/pippki.jar
9c5d914569cc6d6ad6f76e5d49922f69  ./bin/chrome/pipnss.jar
dece066ed0c008b8b909cb350caf739e  ./bin/chrome/installed-chrome.txt
45a0b374ba47f4101940131931e9f3f0  ./bin/chrome/flashblock.jar
e13155c4ae55c45868048a85956b6e88  ./bin/chrome/en-win.jar
cbda35220863d66b6f7c5e8a4def8fda  ./bin/chrome/en-US.jar
a9a2d1f3944bfcd9dbb394ce5e89e04b  ./bin/chrome/comm.jar
8565717ad44ccb30ad94e61e84b4aef3  ./bin/chrome/classic.jar
c30d3ed6e16f1f7583d2dbfcb91526fa  ./bin/chrome/chrome.rdf
7a30577caf70e9465c9350b1781c79b5  ./bin/chrome/aggreg8.jar
430ac070ae609c7618f2b7853e16c514  ./bin/xpcom_compat.dll
6d8b59acdd4e04b1deca02869a8aff1a  ./bin/xpcom.dll
2d4d4c15c89c7b4c80636e4c99e03e8a  ./bin/uninstall.exe
510dcb45b900c4913cfc4376a9b94db5  ./bin/start2.exe
a798e85bfbed0b5eadd20d7a3080f6d1  ./bin/start.ini
bbbc4a04358c4f668c28376446d4a4fe  ./bin/ssl3.dll
35e85604f3929f4b52d584ee24a695ad  ./bin/softokn3.chk
c22d0819a54edffd8f52cc3dc62e7f16  ./bin/smime3.dll
db2b4d0887832f31e84441e0b8ca535f  ./bin/SetDefault.exe
be54ea8f26f625edd04b8d56cef17d12  ./bin/readme.html
531293fdaa8dca2c5b55054d8de5ba41  ./bin/plds4.dll
92cb1b24b80e0ce4514a2fd29f9ec81c  ./bin/plc4.dll
aa6fc338ac7e741fa884adba8bd63315  ./bin/nssckbi.dll
f46e611b8dab76353350e5ce076b88a2  ./bin/nspr4.dll
e74fec2ce0817a76f34392355cdc2df8  ./bin/mozz.dll
cd425a358ba72b6e8cb53f38f2b36c7d  ./bin/mozilla-ipcd.exe
aee5b0b2a11f7aa8c6ef1cdcc455be8c  ./bin/mozctlx.dll
7034982c015c702494ec3cb7b26c3ce5  ./bin/mozctl.dll
f0b4eae4e731873bd3b774c165b2850e  ./bin/License.txt
ed0df4719588a8f05c3e4cac0885fd5c  ./bin/Launch.exe
d758a7d2438036d1984722c97e363a45  ./bin/k-meleon.exe.manifest
e4af16f656a57107ecf2d7946e25b3b7  ./bin/k-meleon.exe
e0dff82ec94cdb47fc1cc69701767bd4  ./bin/jsj3250.dll
dbe820c91b2c24001e8fe14e75cff311  ./bin/js3250.dll
cda0774aef659e851581261ff81ae0e2  ./bin/gkgfx.dll
bb5497bd1832b64297fc44916e923db1  ./cdromupgrade

---

### Post by Stemp on 2007-02-25
??
md5sum file_name.iso

it will give you a checksum. Depending on your version it must be : 

```
283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso

```

---

### Post by gwoodard on 2007-02-25
It is this one
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso

---

### Post by Stemp on 2007-02-25
So the file you've downloaded is good.
If you can start another cd and you burned it slowly, then I really don't understant what's going on :( Sorry

---

### Post by eapache on 2007-02-25
First of all, make sure the cd is in the drive before you power off before trying to boot.
Secondly, I'm not familiar with your BIOS, but I know some have a 'boot menu' option (F12?) at boot that allows you to specify a once-only boot sequence. If that is an option, try that instead of altering the actual BIOS settings. Finally, if you have any other bootable cd (xp install disc, for example) try booting from that. If all of the above fail, I'm afraid I don't know what the problem is, and can't help any more...

---

### Post by Jvos on 2007-02-26
I seem to be having the same problems. I tried burning the iso to dvd and cd.  Neither worked.  I even tried the ultimate edition.  The only time i got to a ubuntu was when I left the Cd in and then came out of windows hibernation but then ubuntu froze.  Any extra help or ideas would be great.

---

### Post by gwoodard on 2007-02-26
> **eapache said:**
> First of all, make sure the cd is in the drive before you power off before trying to boot.
Secondly, I'm not familiar with your BIOS, but I know some have a 'boot menu' option (F12?) at boot that allows you to specify a once-only boot sequence. If that is an option, try that instead of altering the actual BIOS settings. Finally, if you have any other bootable cd (xp install disc, for example) try booting from that. If all of the above fail, I'm afraid I don't know what the problem is, and can't help any more...

Yea my board is a intel BIOS (F2)

---

