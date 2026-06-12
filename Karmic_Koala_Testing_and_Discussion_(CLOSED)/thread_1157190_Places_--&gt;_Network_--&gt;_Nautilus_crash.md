---
title: "Places --&gt; Network --&gt; Nautilus crash"
date: 2009-05-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Toe on 2009-05-12
Whenever I choose Network from the Places menu or from within Nautilus, Nautilus crashes.
All desktop icons disappear for a second, all open file manager windows close.

Is this happening on anybody else's machine?

---

### Post by taavikko on 2009-05-12
> **Toe said:**
> Whenever I choose Network from the Places menu or from within Nautilus, Nautilus crashes.
All desktop icons disappear for a second, all open file manager windows close.

Is this happening on anybody else's machine?

Yes, [http://ubuntuforums.org/showthread.php?t=1156746](http://ubuntuforums.org/showthread.php?t=1156746)
sorry for the confusing title.

---

### Post by thiebaude on 2009-05-12
Yes, this bug 375253 that i filed on monday.

---

### Post by Toe on 2009-05-12
Ah, I see. Thanks for the fast reply.
Hadn't noticed the previous thread about the problem.

I'm glad that the bug status is already set to triaged - shouldn't be too long until this is fixed :)

---

### Post by mdurham on 2009-05-12
> **taavikko said:**
> Yes, [http://ubuntuforums.org/showthread.php?t=1156746](http://ubuntuforums.org/showthread.php?t=1156746)
sorry for the confusing title.

taavikko, my post that you linked to has nothing to do with this bug. Unfortunately this bug occurred around the time that I made my post and therefore was confused with it. What I wanted to know was (when Nautilus is running normally without the current bug) why I can't use the 'Computer' button when I'm root or gksu root.
Cheers, Mike

---

### Post by taavikko on 2009-05-13
> **mdurham said:**
> taavikko, my post that you linked to has nothing to do with this bug. Unfortunately this bug occurred around the time that I made my post and therefore was confused with it. What I wanted to know was (when Nautilus is running normally without the current bug) why I can't use the 'Computer' button when I'm root or gksu root.
Cheers, Mike

Explained in a little bit confusing way..
this bug prohibited access to local or remote mountpoints.
regardless of $USER


You mean you're logged in as a "root", since not much point in doing "gksu root" runned in a terminal?
Example, you press Alt+F2 to get the launcher opened, you then type "gksu root" in order to gain root access? Things don't work that way.

---

### Post by mdurham on 2009-05-13
> **taavikko said:**
> Explained in a little bit confusing way..
this bug prohibited access to local or remote mountpoints.
regardless of $USER


You mean you're logged in as a "root", since not much point in doing "gksu root" runned in a terminal?
Example, you press Alt+F2 to get the launcher opened, you then type "gksu root" in order to gain root access? Things don't work that way.

It appears that I'm not making myself very clear.
If I run 'gksu Nautilus' I CAN'T use the 'Computer' button. If I try to do this I get a message:

"Could not display "computer:"
"Nautilus cannot handle "computer" locations."

It that any clearer?
It's nothing to do with the bug.
Cheers, Mike

---

### Post by davideotape on 2009-05-13
Just tried that out and got this:

```
david@david-desktop:~$ gksudo nautilus

** (nautilus:6017): WARNING **: Cannot extract frame (36, 0) from the grid


** (nautilus:6017): WARNING **: Cannot extract frame (72, 0) from the grid


** (nautilus:6017): WARNING **: Cannot extract frame (108, 0) from the grid


** (nautilus:6017): WARNING **: Cannot extract frame (144, 0) from the grid


** (nautilus:6017): WARNING **: Cannot extract frame (180, 0) from the grid


** (nautilus:6017): WARNING **: Cannot extract frame (216, 0) from the grid


** (nautilus:6017): WARNING **: Cannot extract frame (252, 0) from the grid

[B]Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.[/B]


** (nautilus:6017): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///

(nautilus:6017): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:6017): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
david@david-desktop:~$ 

```

The bit I've highlighted in bold seems interesting.

---

### Post by taavikko on 2009-05-13
> **mdurham said:**
> It appears that I'm not making myself very clear.
If I run 'gksu Nautilus' I CAN'T use the 'Computer' button. If I try to do this I get a message:

"Could not display "computer:"
"Nautilus cannot handle "computer" locations."

It that any clearer?
It's nothing to do with the bug.
Cheers, Mike

Ok, now were at the same page :)

```
gksudo "nautilus --no-desktop computer:"
**
GConf:ERROR:gconf-client.c:1202:gconf_client_key_is_writable: assertion failed: (entry != NULL)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
```

Checked permissions on launchers, evrything seemed fine.

---

### Post by lordbinky on 2009-08-31
This is happening to me too.  This is on Mint 7.  I have a new install only about a week old -not quite fresh as I have installed Dropbox, Codeblocks, VLC, Xdialog/dialog and possible a few more applications.  In the process of troubleshooting another [issue]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498") with Xdialog I may have caused this issue to occur consistently (setting up symbolic links to libcanberra stuff).

Every time I open Network, Computer, or Trash; Nautilus opens for less than a second, all Nautilus windows close, and the Desktop icons disappear.

It used to be intermittent, every 5 or 6 times I open Nautilus, or consistently while cut and pasting files onto an smb share (copy was ok).  Now it is consistently when I open Nautilus as described.

---

### Post by taavikko on 2009-08-31
> **lordbinky said:**
> This is happening to me too.  This is on Mint 7.  I have a new install only about a week old -not quite fresh as I have installed Dropbox, Codeblocks, VLC, Xdialog/dialog and possible a few more applications.  In the process of troubleshooting another [issue]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498") with Xdialog I may have caused this issue to occur consistently (setting up symbolic links to libcanberra stuff).

Every time I open Network, Computer, or Trash; Nautilus opens for less than a second, all Nautilus windows close, and the Desktop icons disappear.

It used to be intermittent, every 5 or 6 times I open Nautilus, or consistently while cut and pasting files onto an smb share (copy was ok).  Now it is consistently when I open Nautilus as described.

This isn't for support place for Mint.
[http://forums.linuxmint.com/](http://forums.linuxmint.com/) Is more appropriate place.

This particular bug is fixed on newer versions of nautilus.

---

