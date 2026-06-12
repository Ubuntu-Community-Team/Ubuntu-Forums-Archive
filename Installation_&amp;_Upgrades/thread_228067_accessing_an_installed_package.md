---
title: "accessing an installed package"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by subiet on 2006-08-02
After i install a package/software through synaptics, how do i know where is it installed and how to access it from which menu, i mean, i can make an educated guess about the location (say if install kino, it must be under the sound/video heading), but still is there a more technical way of knowing it, does synaptics have some sort of reporting system etc.

---

### Post by fourchannel on 2006-08-02
Maybe this screenshot can help you out.

---

### Post by subiet on 2006-08-02
thanks a lot 4channel, that was usefull, another question, i installed the dvbackup, now i know where is the executable (i could also search it through), but the question is, when i click on it nothing really happens, i know i may be sounding like a fool, but any help would be greatly appreciated.

---

### Post by fourchannel on 2006-08-03
Ok, I did some looking into it and I cannot find much documentation on dvbackup. The projects [website]("http://dvbackup.sourceforge.net/") says it's an early stage in development and docs are short.

One of the big changes from windows to linux is that the console comes into play much much more. Infact most programs I use I launch from a console or the almighty "ALT-F2" shortcut.

On the upper left desktop menu, click Applications>Accessories>Terminal

if you type ```
dvbackup
``` nothing happens except that the program does not release control of the prompt. You have to close the program with "CTRL-C" (this works with most console programs, btw).

if you type dvbackup --help you get a VERY brief explanation, but not neccesarily useful.

```
kev@Rei:~]$ dvbackup --help
Usage: dvbackup [OPTION...]
  --version                        show dvbackup version number
  -n, --ntsc-mode                  generate ntsc frames
  -d, --decode                     decode file
  -t, --verify                     verify data
  -b, --set-backup-title=TITLE     set title of backup
  --set-picture=PPM-FILE           set picture of backup
  -v, --verbose                    verbose mode
  -p, --prefix=count               prefix data with 'count' empty frames
  --test=count                     write count test frames - use -t -d to
                                   verify
  -r, --recover                    recover mode
  --enable-audio                   enable full audio headers (read noise mode
                                   ;-) helps with buggy camcorder firmware.

Help options
  -?, --help                       Show this help message
  --usage                          Display brief usage message
kev@Rei:~]$
``` 
but "dvbackup --decode" looks like you probably could use that on a file.

Since I don't have a camcorder I'm gonna take a shot in the dark here and say that this might work.

If I had a Digital Video file called "camcorder_file" then I would decode it using this command in the terminal...

```
dvbackup --decode camcorder_file
``` 
or

```
dvbackup --decode /home/kev/temp/camcorder_file
``` 
Both commands would do the same thing, just the second one shows the complete path to the file.

I hope this helps =D

---

### Post by subiet on 2006-08-03
Thanks for the info on dvbackup but it really didn't help, i want to copy the files from minidv tape in my camcorder to my harddisk, the problem is that i can't see a folder where i can see the files, like i don't know from where should i copy. Kino can capture live stream from camera, but doesn't show the files already in the tape

---

### Post by fourchannel on 2006-08-03
after you plug your camera run this command and post the output here.
```
mount
``` so we can see if/where you camera is attatched to the system.

usually ubuntu (and other linux distros) will mount devices under ```
/media/<whatever>
``` 
So you might have a look there after you plug your camera up.

____

sorry cant be of more help right now, I need to get to bed =D

---

### Post by mlind on 2006-08-03
> **subiet said:**
> After i install a package/software through synaptics, how do i know where is it installed and how to access it from which menu, i mean, i can make an educated guess about the location (say if install kino, it must be under the sound/video heading), but still is there a more technical way of knowing it, does synaptics have some sort of reporting system etc.

```

dpkg -L *package*

```

If package contains .desktop file, then it's usually accessible from menu.

---

