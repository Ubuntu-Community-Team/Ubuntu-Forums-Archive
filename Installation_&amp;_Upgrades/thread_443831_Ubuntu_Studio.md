---
title: "Ubuntu Studio?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by RubberBinder on 2007-05-14
I am using 7.04 currently and I tried to install the repositories for Ubuntu Studio, but after putting in this part **sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'** of the script it says "permission denied"

any help would be appreciated.

:confused:

---

### Post by taurus on 2007-05-14
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and add this line to the end of it.

```
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
```
Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by RubberBinder on 2007-05-16
It's been 2 days, but I tried the above and I still get the same message, here is a screen shot.

[http://i161.photobucket.com/albums/t219/RubberBinder/Screenshot.png]("http://i161.photobucket.com/albums/t219/RubberBinder/Screenshot.png")

---

### Post by taurus on 2007-05-16
I was trying to show you how to edit /etc/apt/sources.list so you could add that line to /etc/apt/sources.list but you kept repeating the same step that you got the initial error.  So, one more time.

From a terminal, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and add this line to the end of it.

```
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
```
Save the change.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by RubberBinder on 2007-05-16
That screen shot was just to show what happened after doing that, but restarting the terminal. Anyway I figured out that I put the line in the wrong spot because I have Automatix and that was the very end. I did it right this time and it worked thanks.

---

