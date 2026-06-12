---
title: "how to set alternate boot path or disk"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by uzee007 on 2011-02-06
Hi Guys,

How can one create an alternate disk or boot path on a ubuntu server? I have a new server running 9.10 and have a full backup of an old server which had all the configuration and installed softwares, etc. Instead of trying to reinstall everything and configure it the way it was, I was thinking of adding another disk to the server, mount it and then hopefully be able to boot it from there. I don't have any LVM or mirroring setup but was hoping if I can specify a secondary boot path when the server boots up, if it fails I should be able to go back to the current one.
Can anyone please help...?

---

### Post by mikewhatever on 2011-02-06
Is the new server installed on a separate hdd? If that's the case, set the bios to boot from it. If it's on another partition, run 'sudo update-grub' from the old server. That should detect the new one and add it as a boot option.

---

### Post by uzee007 on 2011-02-06
Thanks mike. Let me explain a bit more, all the servers are in a virtual environment with virtual disks. Currently the new server is on a new virtual disk and I have a temporary mount point with the entire backup copied on to the temp mount. By entire backup I mean (hopefully) a full server with everything under "/" as it was available from the backup. If I were to add a virtual hdd I can certainly do that and then go into BIOS and then change the boot disk, that sounds easy enough. On the 2nd option, can I ask what you mean by "*run 'sudo update-grub' from the old server*"
The old server is just all files copied onto a mount point, its not a running server, so not sure if I understand it correctly, do you mean run update-grub and then edit menu.lst to include the old server's mount point??

---

### Post by mikewhatever on 2011-02-06
To be honest, I have no experience with virtualising servers. What do you use to boot whatever you boot now? I suppose it would be possible to use the same method with the newer installations.

---

### Post by uzee007 on 2011-02-08
Ok, I added a new virtual disk, created a filesystem and mounted as /tmp_mnt and copied the entire backup of the old server to this mount point. The backup included all directories /var, /etc, /boot, etc. I then rebooted and from BIOS selected the 2nd disk to boot from but it says no Operating system found...
I'm thinking maybe because the original server had a different partition table where /, and /boot and /swap were the 3 partitions, and the new one I created was a plain single filesystem which has all these as directories, maybe that messed it up... not sure though....
anyone has any ideas/suggestions please.... ???

---

### Post by oldfred on 2011-02-08
I do not know about virtual disks either but this may tell something.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

