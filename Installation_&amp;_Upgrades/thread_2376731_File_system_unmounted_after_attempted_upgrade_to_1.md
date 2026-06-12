---
title: "File system unmounted after attempted upgrade to 17.10"
date: 2017-11-05
forum: Installation &amp; Upgrades
---

### Post by bschwartz757 on 2017-11-05
Hello,

I recently attempted to upgrade from Ubuntu 16.04 to 17.10. I've had a dual-boot setup with Windows 10 on a Dell XPS 13 (9360) that has worked great for me for the past year. 

After briefly trying 17.10, I decided to go ahead and upgrade - but when I did, it popped up a warning (it's been a couple of weeks ago now so I don't remember exactly what it was) saying that there was a file system error. 

I attempted some troubleshooting based on google searches, and posted on the support forum but haven't heard anything in a while. I also attempted recovery using gparted (which unfortunately made the Windows portion unusable - I had been able to boot into it, but now I get a Windows Boot Manager screen prompting me to re-install Windows.) I also attempted a repair using Boot-Repair, which didn't fix the issue. I messaged the boot repair folks, who emailed back saying they can't help everyone but if I donated that would help my case - I did that and haven't heard back yet.

The thing about my issue is that I think the partitions are all intact, but just unmounted - I can see them in gparted and using tools like fdisk from the command line (I can still boot in using the Ubuntu 17.10 trial usb.) Unfortunately I just don't know enough about where/how to remount the partitions to get them working again. If anyone could help point me in the right direction, that would be great - I am comfortable working with the command line and would just need some experienced input.

The pastebin output from boot repair is here:
[http://paste.ubuntu.com/25848170/](http://paste.ubuntu.com/25848170/)

And here is output from some troubleshooting commands I've found:

[ATTACH=CONFIG]277423[/ATTACH][ATTACH=CONFIG]277424[/ATTACH][ATTACH=CONFIG]277425[/ATTACH][ATTACH=CONFIG]277426[/ATTACH][ATTACH=CONFIG]277427[/ATTACH]


Any and all help would be greatly appreciated - thanks!

---

