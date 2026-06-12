---
title: "Wine versus Jaunty... regression?"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mykrob on 2009-04-06
I use Wine in Intrepid to run Dreamweaver 8, and it has performed flawlessly.

Testing Jaunty on my laptop, a Gateway M-series, and Dreamweaver freezes with 30-60 seconds of using, and I must force-kill the application. Again, this combination worked fine in Intrepid and Hardy.

I ran it from the terminal and this is the limited output i get:

```

myk@mobileOne:~/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8$ wine Dreamweaver.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f7a0,0x00000000), stub!
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:imm:ImmReleaseContext (0xb01d4, 0x13f740): stub
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
Killed

```

ANy ideas?

Thanks
-myk

---

### Post by Bakon Jarser on 2009-04-06
Did you do an upgrade or a clean install of jaunty?  What version of wine were you running in intrepid and what version of wine are you running now?  Did you reinstall dreamweaver or did you copy it from your old home directory in intrepid?

---

### Post by mykrob on 2009-04-06
Clean installation of Jaunty. Wine version 1.1.18.

I installed Dreamweaver 8 from the CD.

thanks,
--myk

---

### Post by Bakon Jarser on 2009-04-06
I'd suggest looking through this page to see if anyone has had a similar problem:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3482](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3482)

and if your answer isn't there then maybe you'll find a useful link on this page:

[http://wiki.winehq.org/AdobeDreamweaver](http://wiki.winehq.org/AdobeDreamweaver)

and if you still have problems then it might be time to file a bug report with wine.

Edit:  You could also try an older version of wine.

---

### Post by amano on 2009-04-06
> **mykrob said:**
> Clean installation of Jaunty. Wine version 1.1.18

Sounds like a Wine regression. Why don't you try the version from the repos? 

Otherwise it isn't too uncommon, that application x works with 1.1.16 and breaks with 1.1.17. The stable series is rather recommended.

---

### Post by Seventh Reign on 2009-04-06
***Beta*** System + ***Beta*** Program = Some Problems

---

### Post by Bakon Jarser on 2009-04-06
> **Seventh Reign said:**
> ***Beta*** System + ***Beta*** Program = Some Problems

Wow.  You've figured out he has a problem.  Congratulations.  Pure genius.

---

### Post by mykrob on 2009-04-06
no big deal, i really just wanted to see if anyone here was running the same combination of software(s) to see if they had the same issue...

I will try the one from the repository and see if I have the issue. If so, I can just use VirtualBox for a bit and try again after stable is released.. If nothing else, it still works fine on my Intrepid machine.

---

### Post by lachild on 2009-04-13
Did you follow the install instructions or just a streight install from the CD?

If you installed from the cd try these instructions instead:  [http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/]("http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/")

Also if you're on a 64 bit system you need to install odbc32.dll in system folder and odbcint.dll in system32 folder and an override for odbc32 set to native in winecfg.

LaChild

---

### Post by mykrob on 2009-04-14
sorry to have not updated this...

The version from the repository works just fine.

thanks,
-myk

---

