---
title: "Segmentation fault after any update/install"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by bixejo on 2010-05-26
Hi all,

I recently upgraded to 10.04 directly from 8.04 (64bit). Now, any time I update/install/reinstall any package, I get "segmentation fault" in the post-install steps (mainly when processing triggers for whatever, or at the point of "ld[something] deferred processing now taking place").

An example (note I'm trying to translate from Spanish):

```
bixejo@colmena:~$ sudo apt-get install amsn amsn-data --reinstall
Reading package list... Done
Creating dependencies tree       
Reading status info... Done
0 updated, 0 will be installed, 2 to be reinstalled, 0 to be removed, and 0 not updated.
I need to download  13,3MB of files.
0B additional disk space will be used after this operation.
Continue [Y/n]? Y
Des:1 http://archive.ubuntu.com/ubuntu/ lucid/universe amsn 0.98.3-0ubuntu1 [427kB]
Des:2 http://archive.ubuntu.com/ubuntu/ lucid/universe amsn-data 0.98.3-0ubuntu1 [12,9MB]
Downloaded 13,3MB in 21s (613kB/s)                                            
(Reading database...  00%
300369 files and directories currently installed.)
Preparing to replace  amsn 0.98.3-0ubuntu1 (using .../amsn_0.98.3-0ubuntu1_amd64.deb) ...
Unpacking replace for amsn ...
Preparing to replace  amsn-data 0.98.3-0ubuntu1 (using .../amsn-data_0.98.3-0ubuntu1_all.deb) ...
Unpacking replace for  amsn-data ...
Processing triggers for  desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.es_ES.utf8.cache...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Configuring amsn-data (0.98.3-0ubuntu1) ...
Configuring amsn (0.98.3-0ubuntu1) ...

Processing triggers for menu ...
Segmentation fault
bixejo@colmena:~$

```And that's all. :confused: dmesg info follows:

```
bixejo@colmena:~$ dmesg | tail -12
[11568.239198] type=1505 audit(1274905025.094:17):  operation="profile_replace" pid=5683 name="/usr/bin/evince"
[11568.240430] type=1505 audit(1274905025.094:18):  operation="profile_replace" pid=5683 name="/usr/bin/evince-previewer"
[11568.241232] type=1505 audit(1274905025.094:19):  operation="profile_replace" pid=5683 name="/usr/bin/evince-thumbnailer"
[11571.382781] synaptic[5057]: segfault at 0 ip 00007f57469359df sp 00007fff8239fdc0 error 4 in libc-2.11.1.so[7f5746838000+178000]
[11823.021291] apt-get[5885]: segfault at 0 ip 00007f621f9ff9df sp 00007fff66de07b0 error 4 in libc-2.11.1.so[7f621f902000+178000]
[11838.080763] apt-get[6216]: segfault at 0 ip 00007f5178c469df sp 00007fff8143e860 error 4 in libc-2.11.1.so[7f5178b49000+178000]
[11865.903239] apt-get[6580]: segfault at 0 ip 00007f52f2de09df sp 00007fff9763d5a0 error 4 in libc-2.11.1.so[7f52f2ce3000+178000]
[11874.711774] apt-get[7073]: segfault at 0 ip 00007f2cdd30a9df sp 00007fffa223ddc0 error 4 in libc-2.11.1.so[7f2cdd20d000+178000]
[11911.289901] apt-get[7590]: segfault at 0 ip 00007f0be88fd9df sp 00007fff9d632fb0 error 4 in libc-2.11.1.so[7f0be8800000+178000]
[12083.683853] apt-get[7997]: segfault at 0 ip 00007fa829de99df sp 00007fff8b803ed0 error 4 in libc-2.11.1.so[7fa829cec000+178000]
[12162.523799] apt-get[8089]: segfault at 0 ip 00007fe41b5479df sp 00007fff37234530 error 4 in libc-2.11.1.so (deleted)[7fe41b44a000+178000]
[12649.079754] apt-get[8493]: segfault at 0 ip 00007f1f38b529df sp 00007fff736be100 error 4 in libc-2.11.1.so[7f1f38a55000+178000]
bixejo@colmena:~$ 

```I have another computer where I upgraded from karmic to lucid (after a karmic fresh install), and no problem there.

Any clue on this?? :confused:

Thank you in advance,

---

### Post by WinRiddance on 2010-05-26
Might the problem have something to do with your file system?

If you upgraded directly from 8.04 then I'm pretty sure that your file system was still the older ext3 which was changed for the release of Karmic ... where ext4 became the new standard. This would also explain why you had no problem upgrading from Karmic to Lucid since both of these use ext4. If that was indeed the case (that 8.04 had previously been installed in an ext3 environment) then there's no good news for you. Either revert to 8.04 with a backup, or start over on that disk with a freshly formatted ext4 partition. Sorry.
.

---

### Post by bixejo on 2010-05-27
I'm afraid that's nothing to do with ext3 or ext4 filesystems. In the other Lucid system I have (and also in a third one that is not mine but I'm its administrator) all filesystems are ext3 and no problems of any kind there.

Anyhow I appreciate your post and your good will trying to help me, [WinRiddance]("http://ubuntuforums.org/member.php?u=1083274"). :-D

Any other ideas/suggestions shall be highly appreciated!

Thank you,

---

### Post by peterpall on 2010-06-17
Ext4 is nothing but ext3 with some extended features. And as long as you don't start using features that completely aren't part of ext3 (some extended attributes, I think, and really overized filesystems) there actually is no difference in the file system itselves. You are using it as ext4, so it is ext4, and no problems should arise of this.

What *can* cause this kind of problem - and actually caused it on my computer was removing the language pack that provided the current locale (a description of the format of date and time that have to be used and how to sort characters that aren't part of the standard latin alphabet like german umlaute alphabetically.

---

### Post by whit on 2010-07-24
I'm getting segfaults related to libc-2.11.1.so in a fairly new 10.04 32-bit installation. Wasn't happening through the first week of use, but now they're persistent. Googling other reports of trouble with this library suggests either that it has some deep-seated bugs, or that it get's fingered when other stuff built against it has bugs. In my case it's segfaulting on sed, as called during apt-get for some packages, and for update-grub.

---

### Post by pushkarajthorat on 2010-08-14
bump! I am facing this in Kubuntu 10.04(32 bit fresh installation)

related demsg line -
```

[  453.667362] apt-get[2020]: segfault at 0 ip b7590d40 sp bfbae27c error 4 in libc-2.11.1.so[b74b0000+153000]

```
apt-get was working fine until I installed qt creator, and now I dont find its logs!

---

### Post by pushkarajthorat on 2010-08-15
Once again failed!

this time I was installing gedit. Check the attached console logs.

---

