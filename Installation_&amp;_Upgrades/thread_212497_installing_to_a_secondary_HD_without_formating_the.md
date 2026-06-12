---
title: "installing to a secondary HD without formating the whole drive?"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by HeeZy on 2006-07-10
is this possible? i even used acronis in windows to make a linux swap and an ext3 partition, but ubuntu doesn't see any partitions at all on my secondary HD during install. it only sees my secondary HD as one big unallocated space. which is wrong. i have about 5 different partitons on that drive.

so is it possible to install ubuntu on a secondary HD without formatting the whole drive as i already made the partitions.? i don't want to install it on my main drive which holds windows as i don't want to mess it up.

what other install options are available to me for my situation?

---

### Post by raldz on 2006-07-10
Are you using the Live CD? The live CD has a built in partition manager (looks like partition magic for windows).. just choose the "custom" partition when asked.. if you don't have any data yet, just reformat/repartition the whole disk.. from my experience, partitions created with 3rd party apps for Windows is kind of messy.. so I use GParted in Linux to partition my HDs Windows or Linux.. works better..

---

### Post by HeeZy on 2006-07-10
i have the live cd as well as the alternate cd. i do have files on the drive. mostly vids and music. i don't want to delete them and my C: drive has about 12GB free which is not enough to backup my files from the secondary drive.

i just want to install ubuntu to my secondary HD without deleting the other files and partitions.

---

### Post by aysiu on 2006-07-10
For the first drive, mount it some other random place (/windows, for example), but uncheck **reformat**.

For the second drive, create an Ext3 and swap partition and then mount the Ext3 at / and the swap at swap. Then check **Reformat**.

Some more detailed instructions here:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

I would *highly* recommend backing up, though. If you know what you're doing, you should be fine, but you don't know what you're doing. Back up any way you can. Borrow someone's iPod. Burn 100 CDs. Use 200 floppy disks. Do what you have to do.

---

### Post by HeeZy on 2006-07-10
i guess theres no other way then. i'll just have to back up and format.

thanx.

---

### Post by aysiu on 2006-07-10
> **HeeZy said:**
> i guess theres no other way then. i'll just have to back up and format.

thanx.
Well, you don't have to format! I'm just saying to back up just in case something goes wrong.

---

