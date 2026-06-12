---
title: "compiz cant find /usr/local/bin/compiz"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by surfed on 2008-10-02
I just rebooted and compiz no longer works.
A compiz --replace gives me this output:

```
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 415: /usr/local/bin/compiz: not found
```

I checked /usr/bin/compiz and found this line:

```
COMPIZ_BIN_PATH="/usr/local/bin/"
```

so i checked but there is no compiz in local/bin


any Ideas ?

---

### Post by autocrosser on 2008-10-02
Interesting--my compiz is in /usr/bin--I would reinstall & check.

---

### Post by surfed on 2008-10-02
I think /usr/bin/compiz is only the start up script but i could be wrong.
And i did reinstall compiz-core but the problem remains. My Video Setup is fine, xorg log has nothing but good things to say....

---

### Post by RAOF on 2008-10-02
I'd be checking your /etc/xdg/compiz/compiz-manager file.  Make sure that it actually sets COMPIZ_BIN_PATH and such to the right value (/usr/bin)

---

### Post by surfed on 2008-10-02
Yep, 
```

COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"

```

---

### Post by surfed on 2008-10-02
Comming to think of it, why would it be in local/bin there is nothing but a script of mine.... If i change the path in /usr/bin/compiz to /usr/bin/ then compiz cycles its start up message...just looping away

---

### Post by RAOF on 2008-10-02
And you don't have something strange in ~/.config/compiz/compiz-manager ?

---

### Post by olskar on 2008-10-02
This is not fixed yet?

If you open /usr/bin/compiz

> COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/"
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real)


Try changing:
/usr/local/bin/ to /usr/bin/
/usr/local/lib/compiz/ to /usr/lib/compiz/
COMPIZ_NAME="compiz" to COMPIZ_NAME="compiz.real"

---

### Post by surfed on 2008-10-02
> **olskar said:**
> This is not fixed yet?

If you open /usr/bin/compiz



Try changing:
/usr/local/bin/ to /usr/bin/
/usr/local/lib/compiz/ to /usr/lib/compiz/
COMPIZ_NAME="compiz" to COMPIZ_NAME="compiz.real"


Thank you, that did it.

---

### Post by surfed on 2008-10-02
Now what I would like to know is why that affected me and not others....what happened?

---

### Post by RAOF on 2008-10-02
That's a good question.  Something in your setup overwrote the good values in /etc/xdg/compiz/compiz-manager.  Let's see if we can find out what!

Can you post:
[list]
[*]The output of **echo $XDG_CONFIG_DIRS**
[*]The output of **echo $XDG_CONFIG_HOME**
[*]The contents of ~/.config/compiz/compiz-manager
[/list]

It's worth noting that your workaround will be removed the next time the Compiz package gets updated - you still want to work out why it broke in the first place, and fix it :).

---

### Post by surfed on 2008-10-02
Ok, thanks for looking into this, kind of bugs me....

```
echo $XDG_CONFIG_DIRS
/usr/share/ubuntustudio-menu/:/etc/xdg/

```

echo $XDG_CONFIG_HOME
gives me no value

~/.config/compiz/compiz-manager
does not exist
I do have a ~/.config/compiz/compizconfig/config with minimal contents:

```
[gnome_session]
profile = 
plugin_list_autosort = true
```

---

### Post by RAOF on 2008-10-02
> **surfed said:**
> Ok, thanks for looking into this, kind of bugs me....

```
echo $XDG_CONFIG_DIRS
/usr/share/ubuntustudio-menu/:/etc/xdg/

```
...

And we have a winner!  This will expose a (longstanding) bug in the compiz wrapper.  Time to finally go fix it.

---

### Post by surfed on 2008-10-02
> **RAOF said:**
> And we have a winner!  This will expose a (longstanding) bug in the compiz wrapper.  Time to finally go fix it.

So is that a Ubuntu-Studio specific problem? Thats the second thing you have fixed today I believe, glipper being the other no?

---

### Post by olskar on 2008-10-02
This has affected me to (several times) and it is not an Ubuntu Studio problem. 


And as RAOF says the workaround has to be redone every time you update Compiz. Do we know what causes this?

---

### Post by robertc36 on 2008-10-02
it seems that i am having the same problem.
Update totally screwed my desktop.

---

### Post by surfed on 2008-10-06
Todays update of compiz broke it again. Same Fix.

---

