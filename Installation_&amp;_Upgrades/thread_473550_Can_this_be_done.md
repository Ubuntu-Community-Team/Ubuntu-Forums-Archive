---
title: "Can this be done?"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Nortonw on 2007-06-14
Hi All
This is anouther Ubuntu Server Gui install post.

I have read as many as I can find but they all relate to installing the desktop software through an internet connection.

I want to use Server edition in a server enviroment and hence no Internet access FullStop.

How do I install the Gnome or Kde Desktop with out access to the internet?

Someone asked the question before but never got an answer.

I will need a complete noddy guide as I'm rubbish with command line.

Thanks

I do have internet connection for downloading packages etc onto cd but not for the server to connect to.

:(

---

### Post by yota on 2007-06-14
What you want is possible:

1-OnServer)You can have a list of packages to download with:
```

yota@linbook:~$ apt-cache depends ubuntu-desktop
ubuntu-desktop
  Dipende: acpi
  Dipende: acpi-support
  Dipende: acpid
  Dipende: alacarte
  Dipende: anacron
 ....

```
(You can redirect the list to a file with '> filename.txt')
2-OnOtherMachine)Then you can download the needed packages on another ubuntu with 'aptitude download' (or anything else)
3-OnServer)Put the downloaded files in /var/cache/apt/archives
4-OnServer)Install as usual with 'aptitude install *packagename*'

But sincerely this it seems to me a lot of effort... "server environment=no internet access" sounds quite arguable to me. I would surely prefer to get (temporary) internet access through a proxy or a tunnel and then 'aptitude update && aptitude install ubuntu-desktop' and you're done.

Hope this helps!

---

### Post by Nortonw on 2007-06-14
Can the packages from my Kubuntu install be extracted to cd??
Or taken off of the Kubuntu CD to a directory ???

Others must have done this before me?
Surely there's a simple fix?
Perhaps a CD containing stable release packages??

---

### Post by Nortonw on 2007-06-15
OK
Its a new day and I have downloaded new CDs both labelled Alternative at source.

Just tryed them and guess what.

NOTHING :(


Any Ideas?

The packages dont exist for Ubuntu-desktop or Kubuntu-desktop.

Are they caled something else maybe??

---

### Post by Nortonw on 2007-06-15
Ok

After searching through the Kubuntu Alternate Cd manually I have found .Deb file relating to kde.

I ran **Apt-cdrom add **again and then followed it up with **Apt-get install kdesktop**

I also ran **apt-get install kdm **which also installed some file but how do I now start it ??

---

### Post by yota on 2007-06-15
Hi, I'm willing to help, but I'm not sure of where you're trying to get... And you seem to have totally ignored my previous post.
By the way does this help you?
```

yota@linbook:~$ aptitude download kubuntu-desktop
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato in corso... Fatto
Lettura delle informazioni sullo stato esteso        
Inizializzazione dello stato dei pacchetti... Fatto
Costruzione del database dei tag... Fatto          
Get:1 http://archive.ubuntu.com feisty/main kubuntu-desktop 1.32ubuntu1 [15,5kB]
Scaricato 15,5kB in 0s (79,7kB/s) 
yota@linbook:~$ ls
Desktop    **kubuntu-desktop_1.32ubuntu1_i386.deb**  tmp
Documenti  logs_debug                            ubuntu-desktop_1.43_i386.deb
download   scripts                               utils
yota@linbook:~$ 

```
The packages ubuntu-desktop and kubuntu-desktop exist indeed both, but are just virtual packages (let's say just dependancies containers).

---

