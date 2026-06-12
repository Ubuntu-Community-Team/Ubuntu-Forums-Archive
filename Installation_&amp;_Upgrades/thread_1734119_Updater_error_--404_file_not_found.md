---
title: "Updater error --404 file not found"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by LostFarmer on 2011-04-19
Xubunut 10.10 updater says it need to update but get error on downloading.

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1028.49_i386.deb 404  Not Found [IP: 91.189.92.166 80]
    [LEFT]Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3.1_i386.deb 404  Not Found [IP: 91.189.88.45 80][/LEFT]
    [LEFT]Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3.1_all.deb 404  Not Found [IP: 91.189.88.45 80][/LEFT]
    [LEFT]Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3.1_i386.deb 404  Not Found [IP: 91.189.88.45 80][/LEFT]
   
  
```

What is the correct way to correct error?  The files are not at the http: site.

---

### Post by mörgæs on 2011-04-19
You could try changing to another software mirror and reload the package list.

---

### Post by LostFarmer on 2011-04-20
Thanks for the reply.  Tried again this morning and it failed.  Went into Synaptic manager and selected 'all upgrades' , made a download script but it only containd 'wget'.  Tried again and all worked, I did not make any changes in package list.  Have no idea what changed but for now all updates have been installed.

---

