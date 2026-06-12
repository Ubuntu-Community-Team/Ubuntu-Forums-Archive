---
title: "sudo apt-get update broken.. someone help please =("
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by HHP2K on 2007-09-15
Okay. This appears to be a big problem.. that just might have an easy (but not so desirable) solution.

"Sudo apt-get update"

"dpkg was interrupted, you must manually run 'dpkg --configure -a" to correct the problem."

.. okay..

"dpkg --configure -a"

Then, it starts building libraries.. gets to the second one.. appears to be doing a lot of stuff in the background.. and then it stops working. And nothing is displayed. Nothing. 

So I have to restart.

I got the idea to type "sudo aptitude update" and got an ever more serious error:

Bus Error (Core dumped)

oh boy.

So basically, that's the summary of my problem. The only thing I can think of is that the HDD I'm on now is in a newer computer than the one it was in when ubuntu was installed. And it might have just stopped working at around the time I upgraded the computer. Any help guys? :( I need my updates back!

---

### Post by Pumalite on 2007-09-15
Did you go to Synaptic>Edit>Fix Broken Packages?

---

### Post by HHP2K on 2007-09-15
I just tried to run synaptic, and I got this popup:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then it just quits. :\

---

### Post by Pumalite on 2007-09-15
If you know the package names, you can run this: sudo dpkg --remove --force-remove-<packagename>
Take a look at this: [http://ubuntuforums.org/showthread.p...=force+removal](http://ubuntuforums.org/showthread.p...=force+removal)

---

### Post by HHP2K on 2007-09-15
But I don't know what package is doing it, or even if it is a package.. it's just.. doing this for no reason :confused:

---

### Post by Pumalite on 2007-09-15
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

This means that dpkg was in the middle of installing packages. Therefore, there are broken packages that are broken and need to be removed and then re-installed if you want to.
Let's run this:
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install

---

### Post by HHP2K on 2007-09-15
I ran sudo apt-get clean, and it looked like it did it.. didn't put any output though. Then I ran sudo apt-get update and it said the same, dpkg was interrupted.

---

### Post by Pumalite on 2007-09-15
What about:
sudo apt-get -f install

---

### Post by HHP2K on 2007-09-15
Tried that too, gave me the same message. :(

---

### Post by Pumalite on 2007-09-15
Are you able to run: sudo aptitude?

---

### Post by HHP2K on 2007-09-15
When I ran that command, it froze the terminal, cleared all the output, and then displayed "Bus error (core dumped)", and now the terminal isn't taking any input.. :confused:

---

### Post by Pumalite on 2007-09-15
Looks like your system is hosed. Sorry.

---

