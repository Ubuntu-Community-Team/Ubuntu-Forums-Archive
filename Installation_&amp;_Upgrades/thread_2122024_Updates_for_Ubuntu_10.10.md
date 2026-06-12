---
title: "Updates for Ubuntu 10.10"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by Rick B. on 2013-03-03
A few months ago I installed 10.10 on my test laptop and was able to download all the updates through end of life. Today I installed 10.10 on a friend's old laptop and could not download those updates. The error was that it could not fetch the download sites.   :(     Are those updates no longer available? Thanks.

---

### Post by fantab on 2013-03-03
I suppose 'yes, the update are no longer available'. 10.10 reached it '**[end of life' on April 2012]("https://wiki.ubuntu.com/Releases")**. Perhaps when you installed your 10.10 the servers may not have been updated or something like that, but now they are. Install 12.04 *BUNTU or later instead.

---

### Post by Rick B. on 2013-03-04
Thanks, but the laptop I speak of can't handle anything more than 10.10 with only 512 MB of memory. Even Mint 13 with MATE would probably run slow.

Would you know where I could get plugins for WIN Media PLayer and Real Player? All that I was able to install from the repository via Synaptic was the MP3 plugin. Thanks.

---

### Post by sersang on 2013-03-04
First of all i think you should try xubuntu or lubuntu. They are  lightweight distros. But if you wanna stick with ubuntu 10.10 you can  get all updates. You need to edit sources list. ```

sudo gedit /etc/apt/sources.list
```Then change the bold parts [http://**xx.archive**]("http://<strong>xx.archive</strong>").ubuntu.com/ to [http://**old-releases**]("http://<strong>old-releases</strong>").ubuntu.com
You should do that for all lines. Then you can play with your old release.

---

### Post by mastablasta on 2013-03-04
> **Rick B. said:**
> Thanks, but the laptop I speak of can't handle anything more than 10.10 with only 512 MB of memory. Even Mint 13 with MATE would probably run slow.

use Xubuntu or Lubuntu as suggested. Xubuntu will work well on 512MB ram. and it sort of looks like old Ubuntu. you can modify it further to reduce memorry imprint (different theme etc.)

> 
Would you know where I could get plugins for WIN Media PLayer and Real Player? All that I was able to install from the repository via Synaptic was the MP3 plugin. Thanks.
install "restricted extras" package.

---

