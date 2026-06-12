---
title: "[SOLVED] Solving A dpkg Parse Error"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Charlie91 on 2008-06-07
After downloading update packages (I'm using 8.04 version), and just beginning the updating process, power was cut, and the update process was interrupted.  When power was restored, the update manager doesn't work, saying that I type 'dpkg --configure -a' to solve the problem.  I followed the instruction but there's a parse error...

$ sudo dpkg --configure -a
[sudo] password for ...:
dpkg: parse error, in file `/var/lib/dpkg/updates/0034' near line 1:
 field name `

How can I resolve that error? :confused:

---

### Post by iaculallad on 2008-06-07
Display the result of:

```
cat /var/lib/dpkg/updates/0034
```

---

### Post by Charlie91 on 2008-06-07
$ cat /var/lib/dpkg/updates/0034 showed gibberish (it's a binary data file) so I used cat -Ab /var/lib/dpkg/updates/0034:

     1	,y[+M-h^CM-*M-fM-S^GM-^_/[M-l`M-^EM-;M-ZM-xjM-|M-y"ZM-(#M-m^NM-sUM-^C^X^?M-^AM-^PM-I^AM-pCM-MM-^QTM-^V<^T0M-|M-^O-M-YzM-^X7M-ppM-^AM-MdEM-g^XLM-2^EM-KM-^JM-^NM-}6M-^M-s#M-U^EM-%M-&M-^O'^AM-^FM-8M-^GVM-^KM-h^]M-vM-'L^^M->M-^Vw,lM-^WM-^SM-MM-(M-OM-OM-Cf[M-^J_M-6mYyKcY%M-h3M-kM-^NM-VM-\P'[j^CM-DM-eM-#M-s^R\M-vWM-^E^@M-5lMUM-W-M-:2A<M-9r^GM-tM-YM-8M-^HM-I ^NAM-^DM-^_:&M-^PM-*>M-@M-HJM-^DM-quM-vWM-U\4M-vM-KM-^FM-^Fi^NM-hM-!Zm6]M-$M-^N^DD=bM-^H*M-YM-4^ZV^DM-NM-1M-^WM-ZF5M-]M-Q^CL^ZM-VM-+M-^HM-]1^R5_K^EM-^E^SM-DM-yVvM-^EM-^Z^KM-z}LkM-q`,M-,Q@^S"M-`M-%t>M-DM-b^GuM-bM-=M-wM-t=M-^]M-?M-^FM-@M-_zM-_FM-n5^T^QKV/eM-0vM-8^C<OM-^K#mM-^FM-`M-4@sM-.M-'M-1^LM-pOM-UM-%M-'M-G8^@WM-.QM-%M-KM-^G^B8^@{o]"qM-^ZM-vuM-WGM-^P^GM-^G^FIrM-#M-NM-GM-:JM-c|>M-</gvM-6m[TM-J4M-^_M-yM-U}WM-jE^M-eM-^M-gM-kM-*M-HM-^T^FM-tmM-^SM-^@^CM-^BM-.|M-BM-FXM-/M-'^_^SM-'iM-T^EM-*M-^S^C"^W/^UEM-^BiM-= PM-^W^\^@M-%^PcM-iM-dnM-wM-UM-^SM-^MfM-fcM-^PM-rM->!M--M-&^V^P/M-^SM-AVM-^HM-pM-#^BM-=M-MnM-^OM-U}M-^C^Y"VK^D5M--M-^NG0M-^BM-{M-^AEM-ZM-dM-F^CHM-}M-^KM-I$
     2	M-^\^^IM-^N^DM-^\M-ov1=^RM- M-V:M-^AM-wI^@M-f?^AM-%yI|M-WM-S4@M-1fM-"["KM-SM-^E:Y"M-^R^E}M-]E5^^M-DM-odM-M^FM-cMM-p LM-^HM-^WM-pM-wM-SM-?M-^TM-`M-cM-'Q.u0M-m ^Sj$M-YM-^Z^GM-nqM-^WM-S@$1lM-n2^Mh*M-YM-pM-^=^\8^L_M-@M-^^M-oM-JM-JM-^NM-7BM-/j^SM-[M-^Lv1}M-pM-=oUM-PM-^TM-UM-AM-spM-^IM->^]^[kM-1nM-'8w6M-^Q^M^[2^GWM--PM-^HM-tM-0^WM-<M-MM-cx#JM-UEM-!M-<#1M-(f#$
     3	M-z#M-^HM-v^PM-^BM-HM--psM-\^HM-^IOM-QM-=*^AM-UYM-~^Q^IM-(M-^PM-^JgsM-8M-6^M-^_WM-(#IbM-(*M-zw5M-|M-*M-{~b^U^_M-~^ZM-<U*:M-2U^ZM-^F^L^W5lE=^\M-BM-^WM-iM-,M-7M-pM-^^HM-^P'CM-pM-$M-MM-}M-|M--\Y#A/M-iM-AM-:^A-bWM-^U.M-(M-^IM-dM-^OM-R^XM-^L(M-^_M-+M-9M-^GgM-z^IsM-jyYM-=2pM-BM-8S<M-&=M-^LtM-*~M-^GM-%M-XM-*M-^R*5^EM-KM-x~M-FM-rM-kM-^^M-^M1M-NM-PM-^XYM-^_M-^WE#M-:M-&9^MM-q^K^N!M-Yr$
     4	M-DGM-p7XM-OFM-^PaM-D^@M->M-kM-pM-&M-*y7^FdM-UM-^PM-5M-eM-'NM-@M-^AM-3M-)a8M-^^^D^IM-+b]M-^@aM-]^?\M-!M-RM-J.W =M-*M-^T2M-Y6M-|zM-uUC}wM-$M-4^]M-4M-^U^\^LM-E^A^_#-M-cM-4^AM-^[M-RxlM-^[M-xM- ^VM-yM-*mM-UJM-c^ZstM-1M-$X^LM-/S^@HM-|M-)LM-^H-^SppM-}cF^\bM-OM-^QgV:^GGJ^UM-lM-<M-]^U^^fQM-^WvM-\u9x^^_M-^\M-P:M-uvM-pM-2M-h.Iax"M-,iM-S3( ^P-nU_^T^QM- M-hM-FM-p3^Q`M-U{qM-E/^I^@^HM-WM-kM-tM-MM-jtM-9LwM-^F^KAM-^D^R}3^HM-6M-AM-cZM-^HM-H$^B}M-^Wj^\M-5M-X^AM-UM-^@^NM-f"b#M-lM-*M-M"M-B^^\3BvtM-^@h^RuFM-z{MM-^FM-^G$
     5	M-6M-\eM-QM-^L^IM-%M-f)M-RM-6^FjxhM-EqM-P^UM-l^YUM-!M-^N(6^WM-nVM-^FM-1^MM-JM-^LM-0?M-@M-^[M-aM-^DM-KM-)^LM-L^@M-^O|M-eUM-NM-nM-`/_^EkM-^AM-^DM-{M-|M-FM-^S^GM-x/M-=M-Jo9#^]M-^WM-^Q^Pg,M-^\RM-4^QM-|gM-y5^R+M-UM-^WM-@M-hUEM-^LM-ODM-FP$M-|M-1M-quM-pTM-^Q$
     6	M-XfM-8M-^AM-^E3M-lM-6wM-^L^C^NM->M--c^UcYM--xM-fuM-^O^RNM-^WM-SE^NrM-`M-@M-EM-3M-#M-tQ3M-j^UM-=M-?BM- ?^_4M-"^RM-ho^O}M-^]M-A|^?qM-,M-}yM-wM-^D@M-wM-=e^F

Or should I send the actual file through email?

---

### Post by Charlie91 on 2008-06-07
I also did the following to no avail:

sudo dpkg --clear-avail && sudo apt-get update

---

### Post by Partyboi2 on 2008-06-08
You could try removing 0026 and then update again. 
```
sudo cp /var/lib/dpkg/updates/0034 /var/lib/dpkg/updates/0034.bak
``````
sudo rm /var/lib/dpkg/updates/0034
``````
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by Charlie91 on 2008-06-08
Thanks Partyboi2 for that answer but it didn't work, but I found the answer!  For those interested see this [link to linuxquestion]("http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/").  And to summarize:

The power cut caused the corruption of some files, causing problems with dpkg, particularly `/var/lib/dpkg/info/openoffice.org-impress.list'. For some reason, dpkg (or apt-get) can't work if some `.list' files are corrupted; I hope such behavior will get corrected. Why not just ignore a bad file and continue on?

To clear the cache, and other things, `sudo apt-get clean' is good to do. `apt-get update' and `apt-get upgrade' will ferret out the offending file (for me it was `/var/lib/dpkg/info/openoffice.org-impress.list'). So, delete that file and then `apt-get upgrade' again. Then it should work.

Purge openoffice.org-impress (it may be another package for others) and Install it again, perhaps the `.list' file will be restored.

Bye for now.

---

### Post by WSD on 2008-06-09
Similar problem fixed as follows:

Problem:
***********
Fetched 18.5MB in 34s (532kB/s)                                                
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1184 package `xserver-xorg-video-amd':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
**************
fixed as shown in below clip
**********
# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  evolution evolution-common evolution-plugins firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support
  gnome-about gnome-desktop-data initramfs-tools language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libgksu2-0 libgnome-desktop-2 libnspr4-0d libnss3-1d libntfs-3g23 libsmbclient ntfs-3g
  python-launchpad-bugs samba-common smbclient tzdata ufw xserver-xorg-video-cirrus xulrunner-1.9
  xulrunner-1.9-gnome-support yelp
30 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 40.1MB of archives.
After this operation, 410kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
*******************

---

