---
title: "Installation stuck at 95% in Virtual Box"
date: 2009-11-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-11-30
Hi All,

I am not able to complete the installation of daily image of Lucid in Virtualbox. Installation stops at 95%. I have tried with and without network. I am using VB 3.0 on Dell 6400\E1505 and Karmic Please help.

Regards,
SK.

---

### Post by Merk42 on 2009-11-30
Click outside the Virtual Machine (may have to hit right CTRL), then click back inside it again.
I've had that happen then when I do so it jumps to finished

---

### Post by donniezazen on 2009-12-01
> **Merk42 said:**
> Click outside the Virtual Machine (may have to hit right CTRL), then click back inside it again.
I've had that happen then when I do so it jumps to finished

It didn't work for me. My installation never went up beyond 85%. Thanks anyways.

SK

---

### Post by godhika on 2009-12-01
T don't think this is a virtual box problem. When I tried to install lucid (not via virtual box) my installation also got stuck at 95 percent (this was yesterdays daily image- 30.11.09)

---

### Post by Gina on 2009-12-01
I'd heard about problems with yesterday's daily build so I used Sunday's daily.  That went all through.  Maybe today's daily will be OK.

---

### Post by volanin on 2009-12-01
Trying 29.11.09 in virtualbox and got stuck!
#-o

---

### Post by donniezazen on 2009-12-01
I too have tried 2-3 different images. None of them worked.

---

### Post by volanin on 2009-12-02
Workaround until the Lucid Live-CD is fixed:


1. Download karmic Minimal ISO _[here](https://help.ubuntu.com/community/Installation/MinimalCD)_.

2. Boot into the Minimal ISO and select install.

3. Before choosing the language, press ALT+F2 to switch consoles.

4. Press ENTER to activate the new console and type:

```
cd /etc
sed -i 's/karmic/lucid/g' *
```

5. Return to the installation by pressing ALT+F1.

6. Install as normal.


This is the net-install, so all the most recent lucid packages will
be installed and no software updates are necessary after the install.
Another option is to install the karmic live-cd and after that upgrade
to lucid as normal, but it won't be a "clean install".

---

### Post by donniezazen on 2009-12-02
> **volanin said:**
> Workaround until the Lucid Live-CD is fixed:


1. Download karmic Minimal ISO _[here](https://help.ubuntu.com/community/Installation/MinimalCD)_.

2. Boot into the Minimal ISO and select install.

3. Before choosing the language, press ALT+F2 to switch consoles.

4. Press ENTER to activate the new console and type:

```
cd /etc
sed -i 's/karmic/lucid/g' *
```

5. Return to the installation by pressing ALT+F1.

6. Install as normal.


This is the net-install, so all the most recent lucid packages will
be installed and no software updates are necessary after the install.
Another option is to install the karmic live-cd and after that upgrade
to lucid as normal, but it won't be a "clean install".

Hi,

Didn't work either. I am getting following error.

sed : can't move 'brlttymuRx01' to 'brltty': Is a directory

---

