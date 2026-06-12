---
title: "Conky starting automatically???"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-08-18
I'm trying to get conky to run when I log in, but I must be missing something.

I'm using start up applications and adding conky to the list.  It's not starting and as soon as I go to a command-line I can launch it.  Is there a special way to get it to work?

---

### Post by miegiel on 2009-08-18
> **mariner09 said:**
> I'm trying to get conky to run when I log in, but I must be missing something.

I'm using start up applications and adding conky to the list.  It's not starting and as soon as I go to a command-line I can launch it.  Is there a special way to get it to work?

If you're also running compiz you need to add a startup script to delay conky till compiz has loaded. 

```
#!/bin/bash
sleep 30 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky &
```

If you don't use compiz something else is probably going wrong.

also see OP and last posts in [http://ubuntuforums.org/showthread.php?t=1010741](http://ubuntuforums.org/showthread.php?t=1010741) (in hardy *startup applications* was called *sessions*)

---

### Post by chronosMark on 2009-08-18
> **miegiel said:**
> 
```
#!/bin/bash
sleep 30 &&    # 0 good for Xfce - use 20 to 30 for Gnome
conky &
```

I had this working the same way till recently when I changed it to 

```

#!/bin/bash
sleep 30 &&
conky -d
exit

```this way conky is started as a daemon and the script for starting it is exited instead of just staying running in the background.

---

### Post by mariner09 on 2009-08-18
This just doesn't want to work for me.  I have the script created and I made it executable and call in start applications.  It's not launching.  If I run the script from a command-line, it works...

---

### Post by miegiel on 2009-08-19
> **mariner09 said:**
> This just doesn't want to work for me.  I have the script created and I made it executable and call in start applications.  It's not launching.  If I run the script from a command-line, it works...

In the *Startup Applications* did you add *sh your_script_name.sh* or *your_script_name.sh* ?

I've got an icon in my panel to start conky manually, but I just gave auto starting it a shot and it works here.

added to *Startup Applications* :
```
sh .conky_start.sh
```

*.conky_start.sh*
```
#!/bin/bash
sleep 30 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -d -c ~/.conkyrc.bb &
#sleep 0 &&
#conky -d -c ~/Conky/conkyforecast &#!/bin/bash
exit
```

I found 30 sec. to be a bit short though. My desktop barely finished loading when conky started (lots of extra stuff loading). Maybe 60 sec. is a better idea :)

---

### Post by mariner09 on 2009-08-20
I made the modification to start apps by using the sh before the script and it still didn't work.  Might be the timeout value that needs adjusting.

A panel launcher does work...

---

### Post by mariner09 on 2009-08-23
I ended up setting the sleep value to 45 and added the exit at the end of the script.  Between those 2 things it started to work.

---

