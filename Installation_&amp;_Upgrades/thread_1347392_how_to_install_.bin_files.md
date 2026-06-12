---
title: "how to install .bin files"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by da133 on 2009-12-06
I am new to ubuntu, when I was using windows I would just install daemon tools and that would take care of bin files. I tried to install daemon tools on ubuntu using wine but I got error code 256.

How do I install bin files on ubuntu? If I just click on the file I get Could not display "/home/greg/Diablo/DIABLO.bin".

---

### Post by darkod on 2009-12-06
If you are using it trough wine just right-click on the file and select install with wine (or something like that). But I don't think .bin is executable windows file.
As for generally in ubuntu, just execute it with ./filename but if it's not executable file you have to first make it executable with:
sudo chmod +x /path/filename

---

### Post by da133 on 2009-12-06
Do I type that into the terminal? I just did that and this is what happened

greg@greg-desktop:~$ sudo chmod +x /home/greg/diablo/diablo.bin
[sudo] password for greg: 
chmod: cannot access `/home/greg/diablo/diablo.bin': No such file or directory
greg@greg-desktop:~$ 

I'm sure that I typed in the file location correctly

---

### Post by darkod on 2009-12-06
Try using '~' instead of /home/greg. The symbol ~ replaces your home folder. Otherwise there is typing error, the message is clear, it can't find the file of that name where you're telling it to look.

---

### Post by oldos2er on 2009-12-06
> **da133 said:**
> Do I type that into the terminal? I just did that and this is what happened

greg@greg-desktop:~$ sudo chmod +x /home/greg/diablo/diablo.bin
[sudo] password for greg: 
chmod: cannot access `/home/greg/diablo/diablo.bin': No such file or directory
greg@greg-desktop:~$ 

I'm sure that I typed in the file location correctly

 Linux is case-sensitive. ```
chmod a+x /home/greg/Diablo/DIABLO.bin

```

---

### Post by da133 on 2009-12-06
I tried both of those and now nothing happens at all

greg@greg-desktop:~$ sudo chmod +x /home/greg/Diablo/DIABLO.bin
[sudo] password for greg: 
greg@greg-desktop:~$ chmod a+x /home/greg/Diablo/DIABLO.bin
greg@greg-desktop:~$

Also now if I click on the bin file I don't even get an error message, nothing happens

---

### Post by kYd on 2009-12-06
> **da133 said:**
> I tried both of those and now nothing happens at all

greg@greg-desktop:~$ sudo chmod +x /home/greg/Diablo/DIABLO.bin
[sudo] password for greg: 
greg@greg-desktop:~$ chmod a+x /home/greg/Diablo/DIABLO.bin
**greg@greg-desktop:~$**

Also now if I click on the bin file I don't even get an error message, nothing happens

It has worked; you won't get a confirmation message.

Try running it now with ./DIABLO.bin

---

### Post by da133 on 2009-12-06
greg@greg-desktop:~$ ./DIABLO.bin
bash: ./DIABLO.bin: No such file or directory
greg@greg-desktop:~$ ./home/greg/Diablo/DIABLO.bin
bash: ./home/greg/Diablo/DIABLO.bin: No such file or directory
greg@greg-desktop:~$ /home/greg/Diablo/DIABLO.bin
bash: /home/greg/Diablo/DIABLO.bin: cannot execute binary file

---

### Post by da133 on 2009-12-06
I figured it out, I got it to work using binchunker and gmount-iso, thanks for trying to help

---

### Post by ArgentStar on 2009-12-06
Yeah, it's not a binary execuable.  It's an image-file.  You need to mount it as a directory.  Use something like Furius Iso Mount (not a typo) if you want to make it easy with a GUI.

---

