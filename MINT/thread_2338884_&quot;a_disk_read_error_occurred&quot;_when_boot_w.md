---
title: "&quot;a disk read error occurred&quot; when boot windows 7"
date: 2016-10-02
forum: MINT
---

### Post by hydchydc on 2016-10-02
I tried boot repair 
Here is the summary. 
[http://paste2.org/cAkdzsbf](http://paste2.org/cAkdzsbf)


 But still shows the same error

Thanks a lot!

---

### Post by oldfred on 2016-10-02
Moved to Mint sub-forum since not Ubuntu.

I do not see anything specifically wrong. But do not know Mint differences.
You have UEFI hardware, but both Windows & Ubuntu are installed in BIOS/MBR configuration.

You might try fsck on your sda6 partition and then try reinstalling grub again.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

