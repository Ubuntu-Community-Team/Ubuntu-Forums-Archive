---
title: "Optical drive error on install.But using USB."
date: 2019-05-27
forum: Installation &amp; Upgrades
---

### Post by flashbax80 on 2019-05-27
Good morning all. I'm only just getting round to a full ubuntu system, after years of planning to get it done.
Hit a snag after downloading the latest ubuntu, installing via pendrivelinux. I have re-formatted the USB, full format, not just quick. Repeated the process and again same error. The USB drive works with images and MP3 files. I put a few on and dropped them on to the windows laptop. so don't think its the flash drive. I've chosen desktop download option from ubuntu. The universal install option on the pendrive linux site. The installation on to the flashdrive takes a good 20mins, with no errors. Set up the boot sequence to boot from USB on the Ubuntu system, Ubuntu demo desktop loads in everything works fine. Click the install ubuntu, full install, with 3rd party software. And I tried this again choosing minimal install, same optical drive error. I've posted the system specs. I think the system should be fine running Ubuntu.
Any advice would be a real help.

---

### Post by slickymaster on 2019-05-27
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by yetimon_64 on 2019-05-27
> **flashbax80 said:**
> ... I have re-formatted the USB, full format, not just quick...

What filesystem did you format the USB drive to, was it FAT32 or something else?

---

### Post by flashbax80 on 2019-05-27
Fat32. A few quick formats and then a full slow format. Sorry for posting in the wrong place.

---

### Post by yetimon_64 on 2019-05-27
> **flashbax80 said:**
> Fat32...

Yes, that seems OK.

Did you do an integrity check on the downloaded ubuntu iso file or use a bit torrent to download it?
Downloading by bit torrent automatically checks the download file is good. You should always do an integrity check on the downloaded installer if you directly downloaded the file with a browser.

In case you didn't verify the installer iso [[COLOR=#0000ff]--here--[/COLOR]]("https://www.howtogeek.com/246332/how-to-verify-a-downloaded-linux-iso-file-wasnt-tampered-with/") is a "how-to-geek" guide for verifying your download.

If the download turns out to be OK I'd then be looking to try a different USB drive/stick.

---

### Post by flashbax80 on 2019-05-27
Thanks Yetimon. I'll get on that now.

---

### Post by Impavidus on 2019-05-27
According to your system specs, you've got a 0 byte hard drive. Maybe there's a problem with it. [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Sometimes it works for a while, then suddenly stops as it gets warmer or tries to access a particular part of the drive.

---

### Post by flashbax80 on 2019-05-27
yeah its still coming up with the same error msg. With another USB drive. If I've left the boot order as USB only. Will this have the resulting 0 byte problem? I didnt notice that important bit of info. I'll have to sort that out tonight.
Thanks for that Impavidus.

---

### Post by jeremy31 on 2019-05-27
Post results from terminal for ```
sudo parted -l
```

---

### Post by yetimon_64 on 2019-05-27
> **Impavidus said:**
> According to your system specs, you've got a 0 byte hard drive....Good spotting that there Impavidus, I clean missed that particular bit of info.

> yeah its still coming up with the same error msg. With another USB  drive. If I've left the boot order as USB only. Will this have the  resulting 0 byte problem? Its actually now not such a surprise to see a second USB drive failing as well if you have an internal disk problem. Leaving the boot order like you have shouldn't cause the internal drive not to be seen or registering to the system as being 0 bytes. Sorry OP but I simply missed seeing that 0 byte info you posted in the opening post.

---

### Post by flashbax80 on 2019-05-27
Its worked. I'll be honest, no idea why.
I've just done the same format and re-install and it worked.
Thank you all for the help. Now to start actually using and learning ubuntu.

---

