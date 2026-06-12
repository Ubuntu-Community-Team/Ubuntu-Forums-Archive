---
title: "Auto Upgrate from 11.04 to 11.10 Errors"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by bobo123333 on 2011-11-15
[COLOR=black][FONT=Verdana][SIZE=4]Was asked to upgrade to 11.10 by the system.[/SIZE][/FONT][/COLOR]
[SIZE=4][FONT=Verdana][COLOR=black]I accept it the problem began...[/COLOR][/FONT][/SIZE]
[SIZE=4][FONT=Verdana][COLOR=black]First, the setup was not finished - some errors accrue (no details).[/COLOR][/FONT][/SIZE]
[SIZE=4][FONT=Verdana][COLOR=black]The system now is not stable and I cannot always boot (sometimes get black screen).[/COLOR][/FONT][/SIZE]
[SIZE=4][FONT=Verdana][COLOR=black]Now I am logon.[/COLOR][/FONT][/SIZE]
[COLOR=black][FONT=Verdana][SIZE=4]What can I do to fix the unstable situation?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=4]Try to run the upgrade again failed: the reason was: last update was not fully complete.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=4]What can i do?[/SIZE][/FONT][/COLOR]

---

### Post by Miykel on 2011-11-15
[SIZE=3]Had the same problem, downloaded the .iso burned a disk and done a clean install, perfect, well worth the effort, or if you duel boot with Windows, download Wubi, and delete the ubuntu partition, reformat and install via Wubi
  Regards Miykel
[/SIZE]

---

### Post by bobo123333 on 2011-11-15
i have lot of configurations of server applications (including DBs). 
Do not want to install all from begining just to stable the situations.

---

### Post by Miykel on 2011-11-15
[SIZE=2]You may have to reinstall everything, I tried everything but couldn't get the update to work, also some of the apps may not be compatible with the new system  :confused:
Miykel
[/SIZE]

---

### Post by bobo123333 on 2011-11-15
Is not any other solution.... ?
Maybe fix the problems inorder to finish the update 
OR roll back to last stable version.
 
Please help.

---

### Post by jimbabwean on 2011-11-15
> **bobo123333 said:**
> Is not any other solution.... ?
Maybe fix the problems inorder to finish the update 
OR roll back to last stable version.
 
Please help.

If you're really desperate, you could try signing up with Canonical for user support. They are very helpful. The only down side might be that there may not be a solution for your particular issue and then you pay for them to say re-install. I've never known them to be like that though, they've always helped me. [http://www.canonical.com/consumer-services/support](http://www.canonical.com/consumer-services/support)

---

### Post by bobo123333 on 2011-11-15
Thanks, but I will wait to other suggestions

---

### Post by awam66 on 2011-11-15
Try ```
sudo apt-get upgrade -f
```
This will try to fix any errors during your upgrade.

---

### Post by bobo123333 on 2011-11-15
Thanks for the answer.
I tried it and got the following

793 upgraded, 0 newly installed, 0 to remove and 453 not upgraded.
Need to get 0 B/305 MB of archives.
After this operation, 116 MB disk space will be freed.
Do you want to continue [Y/n]? 

I typed Y

and got:

E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

Any suggestions?

---

### Post by bobo123333 on 2011-11-16
What can I do to handle this error:
"E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)"?
 
Is it critial?

---

### Post by raja.genupula on 2011-11-16
open your synaptic manager and then look for util-linux  ... mark it for upgrade and its dependencies . do update and upgrade and then make the move to 11.10 . 

all the best..

---

### Post by bobo123333 on 2011-11-17
The computer boot (by itself) and i cannot logon anymore.
After the bios I see page for a sce with list of items and OK at thr right (probebly part of boot of ubuntu). Then all is balck...
Probebly this is the affect of the "non stable state" of my machine.
 
Please help...

---

### Post by raja.genupula on 2011-11-17
are you getting grub menu , i think you have single OS . Ok , hold shift button while system boot to get grub menu and then choose recovery mode and then choose failsafe or low graphics mode to boot and then do what i have told you in precious post.
all the best

---

### Post by bobo123333 on 2011-11-17
Thanks
The "shift" worked and I was able to logon (BTW, i had there lot of versions: 2.6.38-11 and 2.6.35.25/27/25/24/22 ...can i delete them? ).
I updated util-linux as described and install now the upgrade.
Will report if ok.

---

### Post by raja.genupula on 2011-11-17
> i had there lot of versions: 2.6.38-11 and 2.6.35.25/27/25/24/22 ...can i delete them? )


those are old kernels , if you wanna keep them you can , if you wanna delete them you can . but keeping them will not give you any problems and they gonna useful to you at the time of some upgrade fails.

let me know that is your upgrade went fine or not .

:):)

---

### Post by bobo123333 on 2011-11-17
[LEFT][FONT=Times New Roman, serif][SIZE=2]Thanks for your help.[/SIZE][/FONT][/LEFT]
 
[LEFT][FONT=Times New Roman, serif][SIZE=2]The status is as following:[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=2]I started the upgrade and then reboot[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=2]Since then no normal boot.[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=2]After boot the system is starting and a message "ubuntu is running in low graphics mode"[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=2]Then I asked: what would you like to do: I choose the first option: "Run ubuntu in low graphics mode for just one session"[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=2]After clicking ok I got "Stand by one minute while the display restarts" => "OK"[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=2]And... only black screen.[/SIZE][/FONT][/LEFT]

---

### Post by raja.genupula on 2011-11-17
you did upgrade , we made some progress.

ok actually after upgrade sometimes graphics drivers will give up.

so try to install your graphics or video drivers , i hope that gonna solve the issue.

all the best

---

### Post by bobo123333 on 2011-11-19
I fied all using  "sudo apt-get upgrade -f"
Then i call *startx*  to lunch GUI
It was OK and the desktop seems new 
 
According to system info my system is 11.10
But according to "uname -r" it is 2.6.38.11-generic-pea
 
In addition i cannot access to my apps - not in the new menus

---

