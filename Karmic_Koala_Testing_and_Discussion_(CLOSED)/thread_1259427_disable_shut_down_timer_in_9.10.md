---
title: "disable shut down timer in 9.10"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-09-06
does anyone know of a way to do this. here is how i did it in 9.04 but this will not work in 9.10

[http://bigkidsdidit.co.uk/disable-the-shutdown-timer-on-ubuntu](http://bigkidsdidit.co.uk/disable-the-shutdown-timer-on-ubuntu)

---

### Post by dino99 on 2009-09-06
I'm very surprised as i never seen a timer on my distro(s)  :confused:

---

### Post by cecilpierce on 2009-09-06
I added a "Shut Down" icon to the panel, just right click on the panel and choose "Add to Panel" and pick Shut Down. It worked for me.

---

### Post by Piscium on 2009-09-06
The switch operation I do most often on my PC is suspend. I wanted a way to suspend with a single click. This is what I did.

First created a little C program "mysuspend.c":

int main()
{
   system( "/usr/sbin/pm-suspend" );
   return 0;
}

Then I compiled the program this way
gcc mysuspend.c -o mysuspend

Then I changed the owner and group of mysuspend to root.
Then made it executable and set the UID bit.
Finally added a launcher to the Gnome panel to call it.

And that's it, with a single click the PC is put to sleep.

António

---

### Post by rburkartjo on 2009-09-06
cecil tks for the info that didnt work for me until last update but does the trick. tks

---

