---
title: "Terminal can't execute binairy files."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by -_-' on 2010-04-30
Hello,

I've searched around for similar problems but I couldn't a usefull post.
I just installed Ubuntu 10.xx and I'm new. I want to install Savage2 with the terminal.
So I downloaded a binairy file and and I tried to execute it, but the terminal gave me this error:

```
orangetux@orangetux-laptop:~/Downloads$ chmod 755 ./Savage2Install-2.1.0-x86_64.bin 
orangetux@orangetux-laptop:~/Downloads$ ./Savage2Install-2.1.0-x86_64.bin 
bash: ./Savage2Install-2.1.0-x86_64.bin: can't execute binairy file

```

What's the problem?

---

### Post by ibuclaw on 2010-05-01
Hello and welcome to Ubuntuforums.

First of all, is your system 32bit or 64bit?

You can find this out via typing (or copy and paste) into the terminal:
```
uname -m
```

Regards
Iain

---

### Post by ibuclaw on 2010-05-01
FYI, it looks like you downloaded the wrong Savage Installer file. You most likely have a **32 bit** system, so you need the **32 bit** installer, what you are trying to run is the 64 bit installer, which is incompatible with 32 bit system, hence your system cannot execute the file.

Regards
Iain

---

### Post by -_-' on 2010-05-02
Yes, I've a 32 bit system. Thanks. Now, I'm downloading a 32 bit version. Hope that it works

---

### Post by -_-' on 2010-05-03
Thanks a lot, it worked!

---

