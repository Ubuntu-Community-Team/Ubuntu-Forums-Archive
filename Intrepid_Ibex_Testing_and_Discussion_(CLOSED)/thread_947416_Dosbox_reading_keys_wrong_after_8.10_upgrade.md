---
title: "Dosbox reading keys wrong after 8.10 upgrade"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by The Warlock on 2008-10-14
Hey, I know that this isn't exactly release-critical here, but Dosbox stopped reading my arrow keys after I updated to 8.10. I looked into it and it's reading the up arrow as "printscreen", the left arrow as "left alt", the left alt key as "numpad enter", and the down and right arrows as "unknown key" (which means I can't fix this problem by saving a Dosbox keymap). 

Does anyone have any idea why it would do this or how to fix it? It doesn't seem to be reading the keys incorrectly in any other program.

---

### Post by angryhomer17 on 2008-10-22
Yup I have the same thing going on. Just upgraded to ibex beta a few days ago. It's really pissing me off that I can't finish my game of crystal caves.Every other key seems fine except the dedicated arrow keys. 

In an outside? terminal (ctrl+ alt+ f2) use the command showkey to show the keycodes for your keyboard. I get the following:
key_up "key 103" 
key_left "key 105"
key_down "key 108" 
key_right "key 106"
---------------------------------
Using the dosbox keyboard mapper (ctrl + f1) (in dosbox) and deleting the initial binds and defining new binds results in:

Event:key_up
Bind: Key print screen

Event:key_left
Bind: Key right alt

Event:key_down
Bind: Key unknown key

Event:key_right
Bind: Key unknown key
---------------------------
So I need to get at the dosbox keymapper file. I found:
[http://www.dosbox.com/wiki/Dosbox.conf](http://www.dosbox.com/wiki/Dosbox.conf)

That basically says to use this command in dosbox:
```
CONFIG -writeconf dosbox.conf
```

That results in a dosbox.conf file which resides in your home directory. After restarting dosbox it makes a file called mapper.txt in your home directory.  From the mapper.txt file you find the keycodes:

key_up "key 316" 
key_left "key 307" 
key_down "key 0" 
key_right "key 0"

Neither the key_up or the key_left codes match the showkey codes.

Showkey for right alt (which is bound to the left arrow in dosbox) is actually key 100. For key up the code is key 99.

So, maybe this will be worked out in the final release, otherwise it would be nice to have this worked on.

---

### Post by angryhomer17 on 2008-10-22
Submitted bug report:
[https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/287894](https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/287894)

---

### Post by angryhomer17 on 2008-10-23
[https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/283273](https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/283273) (this bug is a duplicate of that ?)

Check this solution:
[http://vogons.zetafleet.com/viewtopic.php?t=19851](http://vogons.zetafleet.com/viewtopic.php?t=19851)

The solution says:
ubuntu changed something in their keyboard reported keys
create ~/.dosboxrc with contents
```
[sdl]
usescancodes=false 
```

Make sure to remove the mapper.txt file beforehand, otherwise the keys will still be messed up. Also remove the dosbox.conf file and you may even have to reinstall dosbox.

```
sudo apt-get remove --purge dosbox && sudo apt-get install dosbox
```

So, finally it seems to work. Back to finishing crystal caves!

---

