---
title: "How do I make GDM default gnome?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-12
At the moment I have both gnome and KDE installed and the default will always be the DE used last. Is there a way to make it always default to gnome?

---

### Post by Sashin on 2009-10-12
Anoyone know how to do this with the new gdm?

---

### Post by go7Ul1ai on 2009-10-12
> **Sashin said:**
> Anoyone know how to do this with the new gdm?

I wouldn't know

---

### Post by rb0171610 on 2009-10-12
> **Sashin said:**
> At the moment I have both gnome and KDE installed and the default will always be the DE used last. Is there a way to make it always default to gnome?

[http://ubuntuforums.org/showthread.php?t=384195](http://ubuntuforums.org/showthread.php?t=384195)

This is an older post but it may still be relevant.  If you are going to search for additional info I would use the key words GDM + default + session in Google.  The word that you seem to be using in this scenario is DE but login managers such as kdm and gdm refer to KDE or Gnome as a session.

---

### Post by Sashin on 2009-10-12
I've already tried but can't find anything to do with changing it with gdm2. That post didn't help either, the dmrc file was already the way it said, and the first thing referred only to gdm1.

---

### Post by rb0171610 on 2009-10-12
> **Sashin said:**
> At the moment I have both gnome and KDE installed and the default will always be the DE used last. Is there a way to make it always default to gnome?
From:
[http://www.nabble.com/ANNOUNCE:-GDM2-2.8.0.1-%28stable%29,-the-%22Entering-the-Age-of-Aquarius%22-release--td583336.html]("http://www.nabble.com/ANNOUNCE:-GDM2-2.8.0.1-%28stable%29,-the-%22Entering-the-Age-of-Aquarius%22-release--td583336.html")
I copied the most important part:
[I]
The 2.8.0.2 release of GDM2 is a minor release with a few enhancements
and bug fixes. 
- New configuration option AlwaysLoginCurrentSession
   which will automatically switch the user to their
   previous session without asking.  This feature is
   turned off by default.[/I]
I am going to guess since I do not use Gnome or GDM that you would need to edit /etc/gdm/gdm.conf and set AlwaysLoginCurrentSession=TRUE or FALSE.
I am not sure what it says now.  
Good Luck.

---

### Post by Sashin on 2009-10-12
It seems that that file doesn't exist, there are other files in that folder but none of them have the "alwayslogincurrentsession" parameter

---

### Post by ranch hand on 2009-10-12
You may want to look at your /etc/gdm/Init/Default file.  Mine (I only have standard Ubuntu with Gnome) looks like this;
```

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin:$PATH
OLD_IFS=$IFS

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi

sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ "x$XMODMAP" != "x" ] ; then
  if [ "x$GDM_PARENT_DISPLAY" = "x" ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ "x$PROCESSOR" = "xsparc" ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ "x$SETXKBMAP" != "x" ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0

```
If you put mine in gedit and open yours in another gedit you could look at them side by side and see if there is something you can do.

I would rename your current file to Default.OLD and save it before making any changes.  Then after you really screw it up you can go in with the LiveCD or from another OS and change it back.

Makes it a lot less stressful to experiment and therefore more FUN

---

### Post by rb0171610 on 2009-10-12
> **Sashin said:**
> It seems that that file doesn't exist, there are other files in that folder but none of them have the "alwayslogincurrentsession" parameter
Since I do not use Gnome, you can try searching for the file. Open a terminal and type:

*sudo updatedb && sudo locate gdm.conf*

Give it a moment to update the index and search for the file.  If it is indeed on your system it will return the path of the file to you.

[I]sudo updatedb && sudo locate gdm.conf

returns:

/etc/gdm/gdm.conf
/etc/gdm/gdm.conf-custom
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config
[/I]
In ubuntu it is found in the /etc/gdm/ directory. So: 

*nano /etc/gdm/gdm.conf*

I don't think changing this parameter will be what you need but maybe another one in there will point you in the right direction.
Happy Reading.

---

### Post by rb0171610 on 2009-10-12
> **Sashin said:**
> It seems that that file doesn't exist, there are other files in that folder but none of them have the "alwayslogincurrentsession" parameter
From what I understand, several people have complained about not being able to select the default session.  You could always try using KDM as your login manager.  
[I]
sudo apt-get install kdm[/I]

Or you could just deal with the fact that GDM doesn't work exactly the way KDM does.

Good Luck.

---

### Post by Sashin on 2009-10-12
I remember I could do it with the old GDM.

---

### Post by rb0171610 on 2009-10-12
> **Sashin said:**
> I remember I could do it with the old GDM.
Yes. you are not the only one missing this feature. I believe it is avallable in KDM.  You can always convert or resolve lol.

---

### Post by Sashin on 2009-10-12
In a hidden file .dmrc in the home folder it says "session = kde" if I could find out how that's written and change it to session = gnome then it'll mean that default session will always be gnome.

That is, I changed it manually to gnome logged out and default was gnome so if someone knew what writes in the DE into this file then problem solved.

---

### Post by Sashin on 2009-10-12
Anyone knows what exactly edits that file?

---

### Post by rb0171610 on 2009-10-12
> **Sashin said:**
> Anyone knows what exactly edits that file?
Sometime you may see different language encoding in X than on your console (tty) prompt. Sometime two different user need two have different language encodings.
 **~/.dmrc file - Per-user language support**

 In theory this file should be shared between GDM (Gnome) and KDM (KDE), so users only have to configure things once. This is a standard .ini kind / style configuration file. It has only one section called [Desktop] which has two keys: Session and Language. There are some per user configuration settings that control how GDM behaves. GDM is picky about the file ownership and permissions of the user files it will access, and will ignore files if they are not owned by the user or files that have group/world write permission. Normally GDM will write this file when the user logs in for the first time, and rewrite it if the user chooses to change their default values on a subsequent login.
 **Setup language encoding in X**

 Defining LANG variable is not sufficient, you need to setup language encoding using ~/.dmrc file.
cat ~/.dmrc
Output:
 [Desktop]
Session=gnome
Language=cs_CZ.UTF-8

taken from: 
[http://www.cyberciti.biz/tips/gnome-language-encoding-different-than-console.html](http://www.cyberciti.biz/tips/gnome-language-encoding-different-than-console.html) 
Hopefully this helps shed light on the subject.

---

### Post by ranch hand on 2009-10-12
I am afraid that is a KDE generated file.  It does not seem to exist in my menu (Gnome).

You could just try changing it to Gnome and see what breaks, I mean what happens.

Part of the reason that I have as many OS' installed is I would change it to see what happens.  Who ever first said that the greatest threat to your computer security is the operator must of had me in mind.

If you are at your log in screen do you have the choice of KDE or Gnome (along with xterm and Gnome failsafe and, I assume, KDE failsafe)?  That should when you change it call up a box asking if you want that choice set as default.  If it is not then I bet it just isn't in there yet and you may need to wait for another update of GDM or KDM what ever is running your loggin.

---

### Post by ranch hand on 2009-10-12
Frankly, I think you guys are a pain.  Geeze all these goofy ideas.

So here I am, back on my 64bit test platform, installing Lxde on one of my 9.10 installs.  I have got to see how this works.  I am not using KDE for the simple reason that I just don't like it.

The principle should be the same.

---

### Post by ranch hand on 2009-10-12
OK, so I have booted to Lxde and changed from blue to green desktop an saved the .dmrc file;
```

  	 	 	 	 	 	  

 [Desktop]  
 Language=en_US.UTF-8  
 Layout=us 


```
And logged out of Lxde and into Gnome.  I was not asked either time if I wanted to make this the default.


The .dmrc file now reads;
```


[Desktop]
Language=en_US.UTF-8
Layout=us
Session=gnome

```
So it would appear, as suggested by the post from rb0171610, editing this file is not really going to be the thing to do.  It is over written by your selection at login.

See, I didn't worry about this and now you guys have got my knickers in a knot over it.  I'll get over it.

Kind of a neat problem.
Session=LXDE

---

### Post by Sashin on 2009-10-12
Yeah I know that, I was just wondering what exactly was it that wrote the file and if it would be possible to stop it.

Anyway I give up, I don't really need two DEs I was just experimenting so I removed KDE and fixed up my gnome.

---

### Post by ranch hand on 2009-10-12
At least this way you have an OS with a real file manager.

---

