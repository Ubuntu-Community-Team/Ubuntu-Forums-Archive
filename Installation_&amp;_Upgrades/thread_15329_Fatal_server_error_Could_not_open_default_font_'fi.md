---
title: "Fatal server error: Could not open default font 'fixed'"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by offtopic on 2005-02-13
I just installed Ubuntu (downloaded warty ISO) and let the installer download all the security updates.

My system has a Riva128 with 8Mb as video card. When it tries to run gdm the X server crash and gives the message "Fatal server error: Could not open default font 'fixed'". I thought it could be some glx or nv driver problem so I commented out the "glx", the "glcore", and the "dri" module lines and change the video dirver to vesa. 
It didn't worked

Searched around the web (felt lil awkward using links). Some guy solved the problem reinstalling xfs... but as Ubuntu uses Xorg and not XFree that case doesn't apply (or at least that's why i think, am i right?). On a forum read that i should verify if i've got the x-window-system-core package installed, 'cuz in Xorg that's the package that brings the font manager... i did a dpkg -l "*x-window*" and this is what i've got:

root@trashy:~ # dpkg -l "x-window*"
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé
|/ Err?=(aucune)/H=à garder/besoin Réinstallation/X=les deux (État,Err: majuscule=mauvais)
||/ Nom                               Version            Description
+++-==================-==================-====================================================
un  x-window-manager      <néant>            (aucune description n'est disponible)
un  x-window-system         <néant>            (aucune description n'est disponible)
un  x-window-system-core <néant>            (aucune description n'est disponible)
root@trashy:~ #

____
I went a lil further and as the default XF86Config file tries to connect to the unix socket 7100, I did a "netstat --listen | grep "7100" with no results... so there's nothing listening on that port....

At this point i backed the default conf file and ran the old xf86config utility, chose vesa as video driver and the only thing i had to adjust to get a working conf file was the Device option on the mouse' section.

I'm posting here 'cuz i've never walked through that problem before and I would like to know if someone here knows why is this happening and what solution does him/her have... 'cuz I didn't solved it i just found a workaround....

Best Regards.
Offtopic

P.S.: If u ppl needs further information about my system, conf file or logs... don't hesitate to ask.

---

