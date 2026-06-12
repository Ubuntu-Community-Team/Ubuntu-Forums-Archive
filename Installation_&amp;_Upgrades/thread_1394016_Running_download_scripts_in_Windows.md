---
title: "Running download scripts in Windows???"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by kesahli on 2010-01-30
I'm a newbie to Ubuntu, so go easy. Running Hardy Heron.

I can only get dial-up at home and need to install package upgrades upwards of 40MB, so.... pretty much impossible. When needed, I usually generate a download script and individually enter each line into a web browser on my Windows based work computer, which has broadband, saving to a USB drive.

The last upgrade though requires too many packages (230+) to do individually. Is there an easy, quick way to run the download scripts on a windows machine??

Cheers.

K.

---

### Post by DrMelon on 2010-01-30
You can always try writing a Batch File for Windows, and downloading wget for Windows.

To write a batch file, just open notepad or your preffered text editor and write lines like this:


```
wget http://package link

wget http://package link 2
```

Save it as a .bat file, not as a .txt.

Make sure you run it inside the wget folder too.

---

### Post by hyperandy on 2010-01-30
Not sure this is the best way, or if it would work on your work computer for you :p, but you can run wget on windows - windows [http://gnuwin32.sourceforge.net/packages/wget.htm](http://gnuwin32.sourceforge.net/packages/wget.htm)

also another option I was thinking about it is you have the ability to boot into a live cd at work and you could actually save your makings load them in the live version and download the updates and then I think you could then save the downloads or use something like apt-on-cd to move them if I am not mistaken you may want to check that....sorry I may not be much help for you

---

