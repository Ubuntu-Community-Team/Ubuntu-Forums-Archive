---
title: "Can not boot into 6.10 without &quot;ctrl+d&quot; - some filesystem error."
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by brjoon1021 on 2007-01-07
I ran "fsck -y /dev/hda6" and I was told that there was no error in the filesystem - to the best of my abilities to understand what it said after running the command. 

I have only had this trouble with Ubuntu and I have had it with both 6.10 and the previous version. I am a distro junkie, I have 23 installed right now - just because I like it that way. Anyway, I sure would love to be able to boot into Ubuntu properly.

Here is the error that is logged when the failure occurs:

"Log of fsck -C -R -A -a
Sun Jan 7 21:14:42 2007

fsck 1.39 (29-May-2006)
Failed to open the device 'UUID=796e36e7-0fe2-420a-b947-12f3d88693fc': No such file or directory


Replaying journal..
Replaying journal..
Replaying journal..
Reiserfs journal '/dev/hde11' in blocks [18..8211]: 0 transactions replayed
Reiserfs journal '/dev/hdg5' in blocks [18..8211]: 0 transactions replayed
Reiserfs journal '/dev/hda2' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x210b of format 3.6 with standard journal
Blocks (total/free): 3841520/1315088 by 4096 bytes
Filesystem is clean
/: clean, 124635/2000896 files, 6410199/8000336 blocks
Replaying journal..
Checking internal tree..Checking internal tree..Reiserfs journal '/dev/hde6' in blocks [18..8211]: 0 transactions replayed
finished
PCLinuxOS_.93: Reiserfs super block in block 16 on 0x302 of format 3.6 with standard journal
Blocks (total/free): 2560352/1926482 by 4096 bytes
Filesystem is clean
Replaying journal..
finished
Reiserfs super block in block 16 on 0x2205 of format 3.6 with standard journal
Blocks (total/free): 4070448/3221241 by 4096 bytes
Filesystem is clean
Checking internal tree..finished
Reiserfs super block in block 16 on 0x2106 of format 3.6 with standard journal
Blocks (total/free): 2305312/1280702 by 4096 bytes
Filesystem is clean
Reiserfs journal '/dev/hda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
PCLinuxOS_.93: Reiserfs super block in block 16 on 0x303 of format 3.6 with standard journal
Blocks (total/free): 2560352/47924 by 4096 bytes
Filesystem is clean
Failed to open the device 'UUID=f20f336f-cf9f-43b9-aa55-52cb4965428f': No such file or directory


/1: clean, 85058/3843968 files, 638927/3841535 blocks
Replaying journal..
Reiserfs journal '/dev/hda8' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..Reiserfs super block in block 16 on 0x210b of format 3.6 with standard journal
Blocks (total/free): 3841520/1315088 by 4096 bytes
Filesystem is clean
PCLinuxOS_.93: Reiserfs super block in block 16 on 0x302 of format 3.6 with standard journal
Blocks (total/free): 2560352/1926482 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x2205 of format 3.6 with standard journal
Blocks (total/free): 4070448/3221241 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x2106 of format 3.6 with standard journal
Blocks (total/free): 2305312/1280702 by 4096 bytes
Filesystem is clean
finished
Reiserfs super block in block 16 on 0x308 of format 3.6 with standard journal
Blocks (total/free): 3839520/3281485 by 4096 bytes
Filesystem is clean
fsck.ext3: Unable to resolve 'UUID=cb194aea-3d4d-4c0b-91b6-db72934bdedd'

Failed to open the device 'UUID=44ff67d9-f1c0-49b7-ab6c-25c6fe58c201': No such file or directory


Failed to open the device 'UUID=a8534220-6ffe-4427-8c43-f765ae36c5bc': No such file or directory


Failed to open the device 'UUID=9a837a88-d7d2-4727-bb40-9e91db1a0eea': No such file or directory


fsck.ext3: Unable to resolve 'UUID=b0b47546-5bd3-4504-bcb9-1a8511e0b9ff'

Failed to open the device 'UUID=b9bc4248-cb37-49e1-b35a-a72c28665235': No such file or directory


Failed to open the device 'UUID=d69dd768-8c4e-4268-9a2f-7c802bdef919': No such file or directory


Failed to open the device 'UUID=77d6e0fe-4021-4a05-93bd-77957e2278c8': No such file or directory


Failed to open the device 'UUID=8f1c0337-cbb7-4353-95a8-ed9c18364bfc': No such file or directory


fsck.ext3: Unable to resolve 'UUID=0763c348-0bca-4406-99c5-00b5e4875f18'

fsck.ext3: Unable to resolve 'UUID=2f118860-559b-4709-9877-520e4b61938c'

Failed to open the device 'UUID=0286d5c3-7a4b-4c20-b9b5-f7ef0aa09b78': No such file or directory


Failed to open the device 'UUID=7074568a-364d-43bd-8bff-c1bf1418e316': No such file or directory


Failed to open the device 'UUID=ef2f09a4-1704-483e-a485-dfc527aff1c2': No such file or directory


Failed to open the device 'UUID=a3fa0a50-1f87-4b65-b9a4-56a0d2e6e348': No such file or directory


Failed to open the device 'UUID=12b7b5ac-9785-4703-b82e-f94c7d85d62e': No such file or directory


Failed to open the device 'UUID=4e679c04-c356-4889-b85c-fd95ed9fa8bd': No such file or directory


Failed to open the device 'UUID=23183c1f-b190-448d-9b08-b12633ab8a39': No such file or directory


PCLinuxOS_.93: Reiserfs super block in block 16 on 0x303 of format 3.6 with standard journal
Blocks (total/free): 2560352/47924 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x308 of format 3.6 with standard journal
Blocks (total/free): 3839520/3281485 by 4096 bytes
Filesystem is clean
fsck died with exit status 8"

Thanks in advance....

B.

---

### Post by scifan2 on 2007-01-08
verify the uuid in /etc/fstab is correct by booting off of a livecd and run blkid /dev/(yourhdpartition)

---

### Post by confused57 on 2007-01-08
Here's an explanation of the Edgy UUID fstab usage:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

You could just place a # in front of the partitions you don't want to mount in Edgy, or delete the UUID entries, as described in the above link.  I've had this trouble in Edgy anytime I modified another partition that was being mounted at bootup, I only had 10 partitions being mounted.

---

