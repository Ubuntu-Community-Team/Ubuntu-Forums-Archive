---
title: "Applications that need Root Privelages uses different theme"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-04-11
Hello,
Is this happening to everyone else? When you say for example, click on Computer Janitor, it asks for your password but now when it opens up it looks like this:

[img]http://localhostr.com/files/9c19c2/Screenshot.png[/img]

When it should look like this:
[img]http://localhostr.com/files/3050fc/Screenshot.png[/img]

This also happens to other applications that use the policykit framework (I think it's policykit anyway)..

Lee

edit: It's only started happening since I've updated today.

---

### Post by phenest on 2009-04-11
What theme are you using? Is it a 'built in' one, or one you added? Does it happen with all themes? What happens if you change to the Human theme and back again?

---

### Post by go7Ul1ai on 2009-04-11
> **phenest said:**
> What theme are you using? Is it a 'built in' one, or one you added? Does it happen with all themes? What happens if you change to the Human theme and back again?

Ah okay, so it only works on the latest Dust theme I installed, I guess it's not updates. Sorry :/

---

### Post by taavikko on 2009-04-11
The issue lies within that assumption that,
When you launch app with 
sudo: root privileges, users config
gksudo: root privileges, root's config
root's config should be the default, not defined by user.
And this is why you should always launch graphical apps with gksudo...

You can test it with "sudo gedit" and "gksudo gedit"

---

### Post by hexion on 2009-04-11
Check if the theme you're using in your session is installed system wide or just for that particular user.
If that's the case, you can either install it system wide or (easier):

```
sudo cp -r $HOME/.themes /root
```

---

### Post by walmis on 2009-04-11
> **hexion said:**
> Check if the theme you're using in your session is installed system wide or just for that particular user.
If that's the case, you can either install it system wide or (easier):

```
sudo cp -r $HOME/.themes /root
```

better solution: ln -s ~/.themes /root/.themes

---

### Post by go7Ul1ai on 2009-04-11
Cheers guys, that's done the trick :)

[img]http://localhostr.com/files/f4a44a/Screenshot.png[/img]

---

### Post by phenest on 2009-04-11
Actually, system wide themes are in /usr/share/themes

---

