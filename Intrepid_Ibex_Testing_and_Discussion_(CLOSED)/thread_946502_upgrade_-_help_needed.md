---
title: "upgrade - help needed"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ghonz on 2008-10-13
I upgraded my HP Pavilion tx1138ea from Hardy Heron to Intrepid Ibex on friday and I've got a small problem, after I login I get a blank screen and nothing else.
I am able to login to and use the computer through the text box.
Anyone got any help?

---

### Post by jerrylamos on 2008-10-13
I'm not familiar with your hardware.  On my IBM Thinkpad R31 my workaround for a similar problem is:

Boot in recovery mode
Choose root command line prompt

sudo apt-get remove compiz
sudo apt-get remove compiz-core

That did it for me.  Note sometimes it boots to a command line, then I log in and then do 

sudo startx

to get going.  By the way, Xubuntu and Kubuntu both run with no workaround needed.

Jerry

---

### Post by ghonz on 2008-10-15
Didn't work, any other options?

---

### Post by gjoellee on 2008-10-15
i may be a driver problem or a problem with xorg.... You can try run a xfix. Read more: [http://www.kshoster.net/node/18](http://www.kshoster.net/node/18)

---

### Post by dabl on 2008-10-15
> **ghonz said:**
> Didn't work, any other options?

Boot Recovery Mode, choose "Fix X" and then when it is done choose "Resume Normal Boot".

BTW, from the recovery mode root prompt "#" you cannot start the X server with the "startx" command, AFAIK.  You need to start it with ```
/etc/init.d/kdm start
``` which will launch the user login GUI.

---

