---
title: "launch upgrade from terminal"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by romaluca on 2006-10-20
i don't have the graphic
how i can for start the upgrade from terminal?
Thanks

---

### Post by Old Pink on 2006-10-20
What are you upgrading from?
What are you upgrading to? 
What do you mean by "the graphic" do you mean "the image"? 

Have you tried [this]("http://matt.moved.in/?p=30") method, holding Alt, Tapping F2 and typing```
**gksu update-manager**
``` in the box that appears, or ```
**gksu “update-manager -c -d”**
``` for edgy?

---

### Post by aysiu on 2006-10-20
**Step 1:** Install the appropriate *-desktop* package. If you had Ubuntu, it would be *ubuntu-desktop*. If you had Kubuntu, it would be *kubuntu-desktop*. Of course, since you don't have a GUI, that would be... nothing.

**Step 2:** Change your sources.list ```
sudo nano -B /etc/apt/sources.list
``` Replace all instances of the word *dapper* with the word *edgy*. Then save (Control-X, Y, Enter)

**Step 3:** ```
sudo aptitude update
sudo aptitude dist-upgrade
```

Why don't you have a GUI? Are you running a server?

---

### Post by Old Pink on 2006-10-20
> **aysiu said:**
> Why don't you have a GUI? Are you running a server?

I thought by "the graphic" he meant "the image" as in CD Image? :confused:

---

### Post by aysiu on 2006-10-20
I took it to mean a lack of GUI.

romaluca, can you clarify what you mean by > i don't have the graphic?

---

### Post by romaluca on 2006-10-20
i dont have the gui.

the upgrade: 6.06 -> 6.10rc

---

### Post by romaluca on 2006-10-20
I have another problem.I don't have internet.
How i can upgrade from cd? 
Thanks

---

### Post by romaluca on 2006-10-20
i resolved with repository cd
I have launch 
sudo aptitude upgrade 
but terminal tell me this:
The following packages have unment dependecies:
xerver-xorg: Depends: xkb-data but it is not istallable or xkb-data-legacy which is a virtual package.
and other...
How can i do?
Thanks

---

### Post by aysiu on 2006-10-20
I'm assuming you're using the Alternate CD, as that's the only CD you can do a dist-upgrade from.

Type this command: ```
sudo apt-cdrom add
``` This adds the CD-ROM as a repository. Then, type ```
sudo nano -B /etc/apt/sources.list
``` Delete (Control-K) every single line in there *except* the CD-ROM line.

Also, make sure there is only one CD-ROM line.

Then, save (Control-X, Y, Enter). Finally ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

