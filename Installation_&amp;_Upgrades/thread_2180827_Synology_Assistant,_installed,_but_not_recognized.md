---
title: "Synology Assistant, installed, but not recognized"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by hodad on 2013-10-14
I followed instructions in thread:
[http://ubuntuforums.org/showthread.php?t=2112036](http://ubuntuforums.org/showthread.php?t=2112036)

Instructions are well written, I did all of the steps no problem, but still get:
"SynologyAssistant: command not found"  even though it's sitting right there in the SynologyAssistant subdirectory, and is listed as a green executable.  

Any ideas how I can execute the SynologyAssistant file?

Thanks!

---

### Post by tgalati4 on 2013-10-15
Are you sure it is not running?  Perhaps you are getting an error from SynologyAssistant that it can't find a command.  If it is a shell script then you can look at it:

```
cat SynologyAssistant
```

If you get a bunch of gibberish, then it is a binary file.  As I stated in the previous post, I don't have such a NAS (although they are pretty good from what I hear), someone else will have to weigh in who has gotten the assistant to work.  Why do you need it?  Can't you see your shares in the file manager?

---

### Post by hodad on 2013-10-15
"No such file or directory" when I run the above...

Can't see it under "File System" or "Network"   .  Perhaps I could "Ping" it, but don't know which address to look for.   Note, it's connected to my linux box thru my Netgear WNDR4500 router.

---

### Post by hodad on 2013-10-15
Found some good guidance at:
[http://shem-linux.blogspot.com/2013/10/synology-assistant-debian-7-amd64-2nd.html](http://shem-linux.blogspot.com/2013/10/synology-assistant-debian-7-amd64-2nd.html)

It appears that the Synology bin and lib files are expecting 32 bit architecture.    The instructions in the above link don't work for downloading i386 architecture, so I have to figure out a way to do that.   Will keep trying, and post results (if any).   In the meantime, suggestions WILL be accepted on how to proceed!

---

### Post by hodad on 2013-10-15
sudo apt-get install i386 did the trick!   Once I coded it, i386 was downloaded, and Synology Assistant came right up!   It couldn't find my Synology Server thru the router, but I'll tackle that tomorrow.

---

### Post by tgalati4 on 2013-10-16
Wow, that is a lot of work to get a NAS to work.  Glad you got it 1/2 figured out.

---

### Post by hodad on 2013-12-17
Update:
I just configured a new PC with 13.10, and had to go through the whole nightmare again, so thought I'd share some more ideas...

I ran into trouble with the fact that 13.10 AMD (64 bit version) doesn't run the 32 bit SynologyAssistant (as mentioned in previous posts).  I found an excellent posting by Shahin Emil at:
[http://shem-linux.blogspot.com/2013/10/synology-assistant-debian-7-amd64-2nd.html](http://shem-linux.blogspot.com/2013/10/synology-assistant-debian-7-amd64-2nd.html)

After performing the steps he outlined, SA came up.

Curiously, however, before performing those steps, I was able to find the DS-112 by going to Firefox Web Browser (the File Cabinet icon) and looking under "Network", then "Browse Network".  There I found the DS-112 listed as DiskStation.  I was able to open it, and drag/drop folders from the Diskstation to my PC; no need for SynologyAssistant.   

So now I have two methods for accessing the DiskStation, which is nice.

---

