---
title: "Help installing fonts"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by n00blet88 on 2007-09-20
I need help installing windows core fonts. I dont know the terminal command line or the link to donwlaod the core fonts. can some one give me the command or link with installation instructions?

Thanks.

---

### Post by forestpixie on 2007-09-20
it's 

```
sudo apt-get install msttcorefonts
```

---

### Post by Herman on 2007-09-20
Hello n00blet88,
I think that forestpixie has already done an excellent job of answering your question.

Here is even more (superfluous) information about adding fonts in Ubuntu in case it's helpful to anyone, maybe someone else who is searching for info on fonts and runs across this thread. :)

Here's a nice link about fonts for Ubuntu, [300+ Fonts For Ubuntu]("http://ubuntu.wordpress.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/")

Also,  there are instructions In the popular website '[Grokking the GIMP]("http://gimp-savvy.com/BOOK/")', for adding fonts in Linux operating systems here, [Loading Fonts]("http://gimp-savvy.com/BOOK/node12.html#SECTION00844000000000000000") , those are useful too.
Fonts in Ubuntu are be stored in /usr/share/fonts/, if you want them to be accessible to all users and appear in most programs automatically.
For example, if you downloaded sharefont and freefont, from [ftp://ftp.gimp.org/pub/gimp/fonts/](ftp://ftp.gimp.org/pub/gimp/fonts/)  you place the dwonloaded tar.gz packages in your /home/username directory and right-click them and click 'extract here'. Then would do,
```
sudo cp -r sharefont /usr/share/fonts/
``````
sudo cp -r freefont /usr/share/fonts/
```There are also some good programs in 'Applications'-->'Add/Remove Programs' for working with fonts, or try Synaptic or Aptitude.
I have **Specimen Font Previewer**, that's a very handy tool for viewing and comparing all the fonts installed on your system.  I recommend that one to anyone interested in using fonts. It's a great help whenever you need to pick out which font you might want to use.

..and if that's not enough, if you're really keen on fonts you can install [FontForge]("http://fontforge.sourceforge.net/overview.html"), to edit your fonts or even create your own!  :)
(I installed mine through 'Applications'-->'Add/Remove Programs').

Maybe those will help someone,
Regards, Herman  :)

---

### Post by forestpixie on 2007-09-20
it was a bit sparse - :)

---

### Post by Herman on 2007-09-20
> it was a bit sparse - :) Yours was the perfect answer though :)

---

