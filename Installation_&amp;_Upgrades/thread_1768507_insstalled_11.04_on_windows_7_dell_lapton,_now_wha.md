---
title: "insstalled 11.04 on windows 7 dell lapton, now what?"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by a_gonzales on 2011-05-26
Hello!
I really need some help...
I installed Ubuntu 11.04 on my moms dell inspiron laptop with Windows7.
anyways, i selected the 'delete windows and just install ubuntu' option...(something like that)
Now it will get to the login part, and when i login it just has a cursor and backdrop, nothing happens unless i go to SAFE MODE option before entering password.
I need help asap! how can i get it running normally, what did i do wrong?

---

### Post by Hedgehog1 on 2011-05-27
Here is the thread for you:  [http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

It will walk you through the steps to get up and running (you are almost there!)

The Hedge

:KS

---

### Post by a_gonzales on 2011-05-27
so what step do i take?
it loads the login screen, but i have to change the session at the bottom to safe mode
to get into the desktop, if i try loggin in under any other setting, it just shows the wallpaper and cursor.

so what step do i take?  im not at a black screen, i just cant get into the regular ubuntu session, only safe mode..  is there some way to re-install from there? 

what step to take?

thanks in advance...

-a

---

### Post by a_gonzales on 2011-05-27
ok it will let me into classic ubuntu no special effects mode
but i can't get it to recognize my wireless network!!  
when i was installing it, it recognized it right away, what the hell is going on?



im confused....

---

### Post by a_gonzales on 2011-05-27
Ok,   i found the problem, i can't login to the regular ubuntu session because i need 2 drivers
that seem impossible for me to install......

1.)  Broadcom STA Wireless driver
2.)  ATI/AMD proprietary FGLRX graphics driver

i have downloaded these files on my other comp and tried installing them to the dell with ununtu via a sd card but idk what to do, please help!   all i need is to get these drivers going!!!!!!

---

### Post by lykwydchykyn on 2011-05-27
Is there any possible way you can hook to the internet using a wired connection?  That would be, by far, the simplest route to victory here.

---

### Post by ivanovnegro on 2011-05-27
> **lykwydchykyn said:**
> Is there any possible way you can hook to the internet using a wired connection?  That would be, by far, the simplest route to victory here.

Yes and then look for additional drivers from the system settings, in Classic mode you will find it under the category System.

---

### Post by a_gonzales on 2011-05-27
> **lykwydchykyn said:**
> Is there any possible way you can hook to the internet using a wired connection?  That would be, by far, the simplest route to victory here.


how do i do that? i tried hooking the ethernet directly into the machine but it didnt do anything, my other computer is running on wireless......im not sure what to do..

---

### Post by lykwydchykyn on 2011-05-27
Internet access should (in theory) "just work" when you plug in the wired connection.  If you plug in the cable are you able to bring up web pages on the laptop?

If you can get that far, then you can run the drivers tool and get the drivers activated.  If not, then it's probably not worth pursuing that approach.

You might try this to see if it enables your wireless:
```

sudo modprobe b43

```
That will enable an older broadcom driver that isn't as good, but might at least get your wireless jumpstarted long enough to download the real driver.

If that doesn't work, run this command to find out the chipset of your broadcom, that would be helpful to know:
```

lspci |grep -i broadcom

```

---

### Post by a_gonzales on 2011-05-27
ok.... so i plugged in internet but firefox wont work, it says something about security...idk?

when i typed the second command into the terminal it said:

"04:00.0 Network Controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)


thats after i typed in the first command you gave me.....still nothing, 
no wireless.......     when i tried to install it via the system section with the drivers, there was a log error idk.... but it did install my ati graphics driver (still can't use the regular ubuntu session though....im in classic with no effects)


hmmmmm??????  idk..

---

### Post by lykwydchykyn on 2011-05-27
Without at least some portion of the error messages you're getting, it's impossible to ascertain what the situation is on your computer.

---

### Post by a_gonzales on 2011-05-27
the real issue here is that i can't get into the regular ubuntu session, and i can't use my wireless even though i have installed all kinds of different versions of the same driver. the laptop is a Dell Inspiron m5010. i just downloaded Debian and im going to see if that will work......i don't understand why this has to be such a pain in the ***.......

---

### Post by lykwydchykyn on 2011-05-27
I can understand your frustration, and why this would be a major problem.  But nobody can really help you unless you are willing to be more specific about the errors you are getting.

It may be that you're wired internet is working fine, but since I don't know the "security error" you're getting in firefox, I can't say.  It may be that your wireless is actually working, not a driver problem.  Without knowing the error it's giving you, it's impossible to say.

As to "why this has to be so difficult", it's pretty simple.  These are proprietary drivers; whoever wrote them decided (or was forced to decide by a 3rd party) that there should be restrictions on their distribution.  If they hadn't, the drivers would be in the kernel already and things would "just work".   But because they did, they can't be included with a free OS which can be legally distributed anywhere in the world.

Debian is, if anything, more strict about this sort of thing than Ubuntu.  If you're looking for a distro that's more lax about it, maybe Mint or Suse might fit the bill.

---

### Post by a_gonzales on 2011-05-27
ok, just installed debian, now it wont load up the gui, it's just a black command prompt thing that ask for login and password, but then.....idk what to do to get in!!   man........

---

