---
title: "Kernal/partition error on install"
date: 2023-03-29
forum: Installation &amp; Upgrades
---

### Post by crushcrushcrush on 2023-03-29
Migrating from Win 10/11, new to Linux. I've tried ignoring, canceling, I've pressed every key on my keyboard. Refuses to shut off. Not sure where to go from here.

---

### Post by ajgreeny on 2023-03-30
I assume from that image that you have not yet installed Ubuntu but are still trying to do so but we need much more info about exactly what you did.

If I'm correct you can just shutdown the computer and start again.

Did you check the downloaded .iso image file before transferring it to USB?

---

### Post by ActionParsnip on 2023-03-30
Are you setting up a dual boot? If so then you need Windows to be shutdown as the quick boot stuff holds the disk

---

### Post by yancek on 2023-03-30
Try the suggestion in post 3, change fastboot or fast startup in the BIOS, turn it off.  If you are able to boot into windows, go into the power settings and turn off hibernation.

---

### Post by crushcrushcrush on 2023-04-01
Sorry for the delay in replying y'all. TL;DR waited ~hour and was able to restart, changing boot priority fixed the issue and it's running just fine now. 

I was following ubuntu's install guide and selected the option of wiping windows so it was only ubuntu. Basically, my pc was frozen at the photo and not acknowledging any input on-screen, including refusing to shut off which was my main concern. After an hour or so of letting it sit I came back and it was able to shut off like normal. Accessed bios, changed the boot order to prioritize the USB- and that allowed the install to finish. It's been running great ever since, the left-side dock will take some getting used to haha.

>ajgreeny: There weren't any instructions on "checking" the iso, I made sure it was fully downloaded and used the tool recommended by ubuntu's site to transfer it onto the USB, if that's what you mean. If you meant something else, what/how would I be checking for?

---

### Post by ubfan1 on 2023-04-01
Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by yancek on 2023-04-02
> There weren't any instructions on "checking" the iso 

On the Ubuntu download site,  when you click on download you see the page linked below which shows the option "you can verify your download" and clicking on that gives you the needed information. 

[https://ubuntu.com/download/desktop/thank-you?version=22.04.2&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=22.04.2&architecture=amd64)

---

