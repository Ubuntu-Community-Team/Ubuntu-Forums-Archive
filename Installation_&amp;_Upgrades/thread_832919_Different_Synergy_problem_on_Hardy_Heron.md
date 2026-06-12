---
title: "Different Synergy problem on Hardy Heron"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by schmendrick on 2008-06-18
Hi community!

I upgraded to Hardy yesterday. Since then Synergy does not send some special characters like "@" or "{", "~" or "}" between my PCs. charakters like "[" or "(" work though. 

I have Synergy 1.3.1. installed and am using the Synergy client under ubuntu while my Synergy Server is a WinXP machine (also version 1.3.1). I am using keyboard with a german layout. (please note that typing "{", "~"... on a german layout needs the use of the Key called "Alt Gr". So some characters typed in by pressing AltGr + Key are not working, but some are. )

Synergy worked well on Gutsy (only the "~" did not work back then but everything else). 
But now it becomes a major problem: programming without "{" and "}" is not really possible... 

The problem just showed up after the upgrade, so i guess it has something to to with Hardy but not Synergy itself? Plus there were no changes on my XP Synergy server.

I also already tried to reinstall the package, ran the synergy client under root and checked the internet for people with similar problems but did not have any success. I only find some forum entries for synergy being laggy with Hardy. I dont have THAT problem, i "only" have the problem i just described.

Any ideas? I need to get this working so i can code again. If i cant find a solution for this i even would be willing to downgrade to Gutsy again but there should be another solution for this? (And please dont recommend using Ubuntu as the server and XP as the synergy client. That is unfortunately not an option).

if anybody has an idea, i'd appreciate your input!

---

### Post by schmendrick on 2008-06-19
update:

i installed synergy 1.3.0 on both ubuntu hardy and my XP machine now. 
still no success.... 

i only found out one curiosity, not that i think it matters:
when unplugging my keyboard from XP, plugging it in to the ubuntu PC, then plugging it back to XP, synergy will transfer totally different characters for all special characters (chars like "(", "[" )

---

### Post by schmendrick on 2008-06-20
umh... i found a workaround, but a rather annoying one. but here the solution in case anybody else has this problem:

i start ubuntu, log in via ssh, start synergy there via synergyc HOSTNAME to my XP machine. now i go to  my ubuntu via synergy, i then go to 
system->preferences->keyboard->layouts. when i change some things in the layout options, special characters like "{" and "[" wont work but at least he prints out WRONG characters. 

i now close synergy server on XP. i then rerun synergy on XP, via ssh on ubuntu start another session via "synergyc HOSTNAME" (i thought the synergy client would just loose its server and reconnect as soon as it found it again, but it does not) and voilá! special characters like "{" and "@" are working!


[btw. i am still using synergy 1.3.0 but i plan to try it out with 1.3.1.]

---

### Post by djthrawf on 2009-10-20
After some days of search, I think I found a clue to solve such a problem.
Here an extract of the configuration.html file in the documentation :
> [FONT=Lucida Console]shift = {shift|ctrl|alt|meta|super|none} 
ctrl = {shift|ctrl|alt|meta|super|none} 
alt = {shift|ctrl|alt|meta|super|none} 
meta = {shift|ctrl|alt|meta|super|none} 
super = {shift|ctrl|alt|meta|super|none}  [/FONT]

Map a modifier key pressed on the server's keyboard to a different modifier on this client. This option only has an effect on a client screen; it's accepted and ignored on the server screen.  
You can map, say, the shift key to shift (the default), ctrl, alt, meta, super or nothing. Normally, you wouldn't remap shift or ctrl. You might, however, have an X11 server with meta bound to the Alt keys. To use this server effectively with a windows client, which doesn't use meta but uses alt extensively, you'll want the windows client to map meta to alt (using [FONT=Lucida Console]meta = alt[/FONT]). There an extract of my config file :
> section: screens
    ubuntu_screen_name:
        meta = alt
        alt = super

    winXP_screen_name:
endI have a French keyboard with same kind of special keys as yours. Synergy serveur runs on WinXP and client on Ubuntu 8.04. This solution allows all special characters using AltGr key.
Now, characters as é,è,à,£,µ and ç are still a problem and are not usable. If someone has the solution...

---

