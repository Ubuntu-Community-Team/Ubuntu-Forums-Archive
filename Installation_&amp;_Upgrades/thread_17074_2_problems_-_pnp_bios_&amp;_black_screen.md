---
title: "2 problems - pnp bios &amp; black screen"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by cronos01101x5 on 2005-02-25
Ok so I just installed ubuntu. and well I have 2 problems.
first let me say... I am completely new to Linux.. Never worked with it before, so I know nothing.

when i boot up ubuntu it gives me some message about a fatal error with the pnp bios and tells me i should reboot with "nobiospnp" 

uh... how do i input the command? 

I went into my bios setup, and there is nothing there that helps.

ok second problem is the black screen thing i saw a few other people post about.

if i do ctrl+alt+f1 i can login, but unfortunately i don't know any of the commands to be able to get to the file to edit it (/etc/x11/xf86config-4)

i tried to copy do a copy/paste from the one on the live cd as some people had mentioned, but It says i don't have write permissions, so i can't do that either.

i don't know how to get past that

save me jebus!!! :P

hehe some help would be really nice

am I a newb or what!! hehe

---

### Post by trivialpackets on 2005-02-25
when i boot up ubuntu it gives me some message about a fatal error with the pnp bios and tells me i should reboot with "nobiospnp" 

uh... how do i input the command? 

         [COLOR=DarkRed]When you get to the GRUB command screen, highlight ubuntu, probably default and press 'e'.  That will bring up a mini menu if you will.  Go to the second line, press e again and add your nobiospnp to the end of this line.  press return and then press 'b'.  
         Once you get booted up, you can sudo gedit /boot/grub/menu.list and add the command nobiospnp in the same place that you added it originally.  You'll see what I mean when you scroll down and see the same menu that you scrolled through as this is the config that displays that.[/COLOR]

I went into my bios setup, and there is nothing there that helps.

ok second problem is the black screen thing i saw a few other people post about.

if i do ctrl+alt+f1 i can login, but unfortunately i don't know any of the commands to be able to get to the file to edit it (/etc/x11/xf86config-4)

i tried to copy do a copy/paste from the one on the live cd as some people had mentioned, but It says i don't have write permissions, so i can't do that either.

          [COLOR=DarkRed]did you sudo cp?  I don't like it when it doesn't give you permission....if not sudo chmod 777 <directory>  and hopefully that will resolve your permissions.  Also, when you get it working, run:
sudo cp /etc/X11/xf86Config-4 /etc/X11/xf86Config-4_backup
to make a backup.  It's saved me many times already.  Enjoy.[/COLOR]

i don't know how to get past that

save me jebus!!! :P

hehe some help would be really nice

am I a newb or what!! hehe[/QUOTE]

---

### Post by cronos01101x5 on 2005-02-25
thanks!!! I'll give this a try

---

### Post by cronos01101x5 on 2005-02-25
Ok so that didn't really work.... so I kinda winged it :P

what i did instead was i used sudo editor

that did the trick

I had a few other minor problem, which i solved once i got logged in.

Thanks anyway for the help!! :-)

---

