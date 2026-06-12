---
title: "/etc/apt/sources.list.d/google-chrome.list changing?"
date: 2016-03-07
forum: MINT
---

### Post by ogp on 2016-03-07
Hi, 

When I run the #sudo apt-get update && sudo apt-get upgrade  command I've had the (fairly common) error of late as follows; 

```
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Following on-line instructions led me to add " [arch=amd64] " into the /etc/apt/sources.list.d/google-chrome.list file, so that it reads as follows; 

```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

```

Once this is done the update and upgrade commands run fine. 

However I have found that the google-chrome.list file later reverts to it's original form - i.e. without the additional part, which means that the update and upgrade commands fail again. 

This sounds very odd but it's happened three times now and I don't think I am dreaming it! 

What can I do to stop the file from reverting to it's earlier form? 

Thanks, in advance, for any help. 


Oli.

ETA: I'm running Mint 17.2 Rafaela 64-bit version.

---

### Post by howefield on 2016-03-07
Thread moved to the "*MINT*" forum.

---

### Post by ogp on 2016-03-07
Thanks for moving the thread howefield.

---

### Post by howefield on 2016-03-07
You're welcome.

Try [this thread]("http://ubuntuforums.org/showthread.php?t=2316173") for the solution.

---

### Post by slickymaster on 2016-03-07
> **ogp said:**
> Hi, 

When I run the #sudo apt-get update && sudo apt-get upgrade  command I've had the (fairly common) error of late as follows; 

```
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Following on-line instructions led me to add " [arch=amd64] " into the /etc/apt/sources.list.d/google-chrome.list file, so that it reads as follows; 

```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

```
<---snip--->
That gets reset. To fix the source, you need to run```
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/etc/apt/sources.list.d/google-chrome.list"
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/opt/google/chrome/cron/google-chrome"
```

---

### Post by ogp on 2016-03-07
Guys, 

Thanks! Both for the link to the other thread (and now I feel a fool for not having seen that in the first place!) and for the solution posted by slickymaster. 

Why does the cron job reset the file I was modifying? What was the reason for there to be such a cron job set up? 

Thanks again. 


Oli.

---

### Post by slickymaster on 2016-03-07
Apparently, the **/etc/apt/sources.list.d/google-chrome.list** file gets reset by the Update Manager. The fix of editing the text file itself seems to be reverted when you restart your computer.

See [http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html](http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html)

---

