---
title: "Please Help- Getting ffmpeg and dvdrip errors"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aura eyes on 2008-10-17
Greetings,

    Ibex is great so far, but I have a problem converting video files.

I've tried ripping the sound out of a file with ffmpeg (which always used to work) with the following code:

ffmpeg -i video.avi -vn sound.mp3

Unfortunately, I get this error:

ffmpeg: error while loading shared libraries: libx264.so.57: cannot open shared object file: No such file or directory

Also with dvd:rip, I can rip the dvd into vobs fine, but when I try to transcode to avi, I get this message:

[transcode] warning : libx264.so.57: cannot open shared object file: No such file or directory



Surely, they're related, but I don't know how to fix this.  Any help would be appreciated.  I'm running 64bit Ibex.

Thank you.

---

### Post by ronacc on 2008-10-17
open synaptic and use the search button ( not quick search ) to search for libx264  and make sure its installed , if it is, try reinstalling it ,if not install it .

---

### Post by aura eyes on 2008-10-17
I have libx264-59

libx264-57 is available.

Should I completely remove libx264-59 and install libx264-57?

Thanks for the quick reply.

---

### Post by ronacc on 2008-10-17
you can have both , just install libx264-57 , they dont conflict .

---

### Post by aura eyes on 2008-10-17
Thank you so much!  I'll be able to do it in a couple hours (not home right now).

Thanks again for the help..... I'll update the results later.

---

### Post by aura eyes on 2008-10-17
Ugh!

Unfortunately, I get this error message:

Package libx264-57 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


So I tried the terminal and this message came up:

Package libx264-57 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libx264-57 has no installation candidate


-sigh-


Hopefully there's a way to fix this.  Perhaps adding a source to my sources list?  I only have the canonical ones and medibuntu ones activated right now.

---

### Post by aura eyes on 2008-10-17
Yesssssss!!!


I finally got it to work by using the hardy repos.

Thanks for all your help, ronacc!

:-)

---

