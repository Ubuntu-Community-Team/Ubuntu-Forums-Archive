---
title: "linux is running but can't be rebooted"
date: 2021-10-21
forum: Installation &amp; Upgrades
---

### Post by lihkgman721 on 2021-10-21
I am running the ubuntu 16.04.3 LTS, which was originally launched as an OpenStack instance. 
The OpenStack was removed accidentally due to some reasons.
But the instance keeps running and many things have been installed into it. 
However, I can't reboot it now. Otherwise I won't be able to boot into it afterwards.
What can I do to fix this? Below is the boot info from the Boot Info Script.
Thank you very much in advance!

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================




============================ Drive/Partition Info: =============================


no valid partition table found
"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/vda1        971361cf-eca4-4598-be96-fd9585aa93fe   ext4       cloudimg-rootfs
/dev/vda14
/dev/vda15       7038-1F67                              vfat       UEFI
/dev/vdb         72a0596b-11ac-48c9-b976-1a48a3359055   swap


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/vda15       /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/vda1        /                        ext4       (rw,relatime,data=ordered)




=============================== StdErr Messages: ===============================


mdadm: No arrays found in config file or automatically



```

---

### Post by QIII on 2021-10-21
16.04 is beyond its End Of Life (EOL) and is no longer supported except for Extended Security Maintenance (ESM) if you are using that.  Software updates are unavailable if you do not know how to access them and you won't get any security updates without ESM.

Right now you are on life support.  Back up, back up, back up.  So long as your present instance is currently running, you should be able to locate and back up your important data. Salvage everything you can in case everything goes sideways.

I would highly recommend that you find a way to do a clean installation of the most recent LTS (20.04) in another OpenStack instance and then restore your important stuff.    Until then, it is likely an unwise use of your time -- and that of the community -- to expend too much effort on a solution.

---

### Post by ActionParsnip on 2021-10-21
I suggest you create a new server using 20.04 and restore your user data to that. You could even update to 18.04 from your 16.04 installation but you will need to check for any gotchas this may cause. A clean install will give a pristine OS without the old cruft from the old version. Feels like a new sweater

---

### Post by guiverc on 2021-10-21
Your system can't be upgraded (to 18.04) until all updates have been applied; and you're well behind on upgrades & security fixes, as a *fully* updated *xenial* or 16.04 system will report itself as being 16.04.7.

See [https://fridge.ubuntu.com/2020/08/14/ubuntu-16-04-7-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-16-04-7-lts-released/)

To have a system that reports itself as 16.04.3 implies you've not applied security fixes since before [1 March 2018]("https://fridge.ubuntu.com/2018/03/03/ubuntu-16-04-4-lts-released/") as that is the ISO release date for 16.04.4, and installed systems upgraded to 16.04.4 before that date via normal upgrades.

As already stated though, [Ubuntu 16.04 LTS is end of *standard support* though ESM support is available]("https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/")

---

