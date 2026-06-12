---
title: "Installation Problem"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by cosmicravi on 2007-09-05
Hi Viewer,

I have got a Ubuntu 7.04 Server Edition from my friend which I was trying to install on my laptop. 

I managed to install the OS but when starting it, my laptop just hangs at the starting stage at 

"Executing local scripts from rc.local      [ok]"

Kindly guide me what I should do?

My laptop configuration is Intel Celeron M 1.73 GHz with a 512 MB RAM and a 80 GB hard drive. 

Thanks,
Ravi.

---

### Post by southernman on 2007-09-05
Just hit the enter key for the login prompt.

---

### Post by cosmicravi on 2007-09-06
Hi,

I appreciate you for spending time to reply my post.

I have tried that option of hitting the enter key.

The keyboard just jams. And the display hangs. 

Any other ideas?

Thanks,
Ravi.

---

### Post by southernman on 2007-09-06
Sorry Ravi, that's worked for me in the past. If I recall correctly it has something to do with the way the init.d scripts are loaded, and their order of loading.

If you feel like it, you could try the 6.06.1 (Dapper LTS) server version. It loads properly and drops you into the login prompt as you would expect.

Takes me about 30 minutes to install Dapper on my old PII 350... yours should go much quicker.

---

### Post by cosmicravi on 2007-09-06
Hi,

No problem. You do not have to apologize. You gave your try to solve my problem. That is really great. 

But I have a query, is there something like Ubuntu 7 Server Edition will not work for Intel Celeron 1.73 GHz processor with 512 MB RAM, as I seriously believe that there it has got some problem.

I even tried Fedora latest version and the system has hanging similarily at installation stage itself.

Thanks,
Ravi.

---

### Post by southernman on 2007-09-06
Just a swag here Ravi (scientific wild a** guess), sounds as if you have hardware issues, more than software.

What is the last OS you had running on this box?

I'd let the box run on memtest86 for several hours to get a good test of your memory... as a starting point. Most installation and LiveCD's have the memtest option on them, just page down to the selection and hit enter. Letting it run for a short time, is as good as not running it at all, so let it run for several hours if not 1/2 to 1 day. If you see a lot of errors in the results, its a pretty safe bet you found the problem.

The Dapper release I suggested is an older release that, for me at least, works perfectly. Here is a direct link to the download of this server installer...

[http://releases.ubuntu.com/6.06/ubuntu-6.06.1-server-i386.iso]("http://releases.ubuntu.com/6.06/ubuntu-6.06.1-server-i386.iso")

---

### Post by cosmicravi on 2007-09-06
Hi,

Thanks man, will run and let you know the results. 

Regards,
Ravi.

---

### Post by cosmicravi on 2007-09-06
And by the by, I was previously running a Red Hat Linux 8.0, Windows XP also. 

I never experienced these problems before. Will let you know the results of the memtest86.

Thanks,
Ravi.

---

