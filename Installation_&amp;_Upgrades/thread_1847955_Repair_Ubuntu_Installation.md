---
title: "Repair Ubuntu Installation"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by bjm904 on 2011-09-21
So I had Ubuntu Desktop 11.04 installed dual boot with windows 7 and I wanted to play around with Ubuntu server so I was trying to install Ubuntu Server in another partition but it installed in the same partition as Ubuntu Desktop and now when I choose Ubuntu Desktop to boot to the screen is just black. I can boot older versions of Ubuntu Server abd Windows 7 but Not Ubuntu Server current or Ubuntu Desktop. I have a live CD to boot to. I would like to repair my Ubuntu Desktop and Remove Ubuntu server without causing any personal data loss.

---

### Post by vinterkind on 2011-09-22
Have you just tried to install Ubuntu Server or have you done it ?
How come that you can boot older Ubuntu Server Versions ?

Surely you know, that if you've installed Ubuntu Server on the same partition you've deleted
all your previously installed data. I may guess it would be very difficult to rescue anything then.

Could you post your partition layout with comments ?
```

fdisk -l /dev/sda 
```or something.

cheers,

---

### Post by bjm904 on 2011-09-22
I use a program to read ex4 from windows and my files are still there. Im not sure what happened. Is there a command I can use to uninstall ubuntuserver?

---

### Post by vinterkind on 2011-09-23
That is, why I need your partition layout. 

If your /home directory is on a different partition you could easily install ubuntu desktop on your / again.
If you installed Ubuntu Server and combined both of your systems, please rescue all your data and I'd suggest you to install your desktop version from scratch.

As for your question, I must say No. There is no program to uninstall Server as-is and rescue your
old desktop system. Like the old saw ...

"*Unix is user-friendly. It just isn't promiscuous about which users it's friendly with.*"

cheers,

---

### Post by bjm904 on 2011-09-24
I would love to keep all the packages I installed. What folders can I keep? How much will I loose.

---

### Post by logiblocs on 2011-09-24
If you can copy the files from Windows and back them up then you should be able to restore most things - however it may just be easier to back up the package selection for you programs.

Make sure that the files you can see are actually Desktop files not just the server ones.

---

### Post by bjm904 on 2011-09-24
What folders should I backup?

---

### Post by vinterkind on 2011-09-26
First you could save the programs - maybe - with 

dpkg --get-selections

they should've been installed into the /usr/ path.

then you should save your home directory and be aware of securing your hidden folders too.
(the ones with the preceding dot, you can see with ls -a)

So If you're lucky you may not lose too much.

---

### Post by oldfred on 2011-09-26
If you can drill down to your install this may work or chroot into your system and use dpkg.

All the data on what packages are installed is contained under the /var/lib/dpkg/ directory.
It's all in the status file - every installed package has the word "installed" on it's Status: line.
However, it's probably easiest to just get the directory listing of the /var/lib/dpkg/info/ directory. Just look at all the files named *.list:
cd /var/lib/dpkg/info
ls *.list | sed 's/\.list$//'

If you can chroot into it:
 dpkg --get-selections > ubuntu-files

Post full boot script to see what is installed where. I use this regularly with multiple installs and multiple drives just to docuement what is where and lots of details of installs.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by bjm904 on 2011-09-26
which folders do i need to back up?

---

### Post by oldfred on 2011-09-26
For a regular backup or your packages?

---

