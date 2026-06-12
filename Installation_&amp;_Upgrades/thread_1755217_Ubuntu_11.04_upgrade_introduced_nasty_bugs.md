---
title: "Ubuntu 11.04 upgrade introduced nasty bugs"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by ubix on 2011-05-10
After installing the latest 11.04 Ubuntu upgrade from Maverik to Natty, beside a huge disappointment with both of the two new GUI shells, a few nasty surprises cropped up: 

[LIST=1]
[*]Evolution mail lost my address books 
[*] Folders and Trash inaccessible
[*] Inaccessible international keyboards
[*] No place for hardware indicators on tje panel
[*] Control icons in notification area disappeared
[*] Skype notification icon disappeared
[*] In Unity dock "Open in new Window" <Ctrl+N> is missing for many applications 
[*] Workspace control in Unity is much worse now
[*] Mouse R-click in some apps (i.e. Text Editor, FireFox) occasionally totally insensitive  
[*] Selecting GUI shells should be more aggressively advertised
[/LIST]

A few of the above list are not really the bugs, I explain the above items a bit more on my web page. 
You can check it out here: [Ubuntu 11.04 (Natty) upgrade introduced nasty bugs and flaws]("http://sloveneti.tripod.com/rac/public/public_Natty-upgrade-nastyBugs.html")

The most disturbing is the loss of data in Contacts namely almost all, except the most recently used address books in Evolution email are lost. It looked as if the upgrade wiped out large portion of directory structure under ~/.evolution directory branch. I have found the missing files though in a different place namely under ~/.local/share/evolution. Somebody must have reorganized the directory structure, however they have not propagated all the changes to the application level setups!

A similar problem pops up with the Trash, as well as with the file access to folders in that reside under Places on the panel in Ubuntu Classic. One does not have access to these items. Since I also found Trash directory structure under the ~/.local/share I believe the problems with address books in contacts exhibit similar symptoms.

Second worse or even worse than that is the loss of multi-lingual abilities on Ubuntu. All the above is true for all available display managers, so it must be related to the Natty itself! Please, responsible folks at Ubuntu address these problems as soon as you can! We have never in Unix/Linux history been so disappointed with a regular release of OS!

For the past few days I was hoping, that our old friend Upgrade manager, will correct some of the most obvious and pressing problems, but slowly I am getting impatient, and i am seriously thinking to switch back to Maverick, and freeze this release indefinitely!

Can someone please tell us if there is a chance that at least the most obvious of some of the above flaws will be soon addressed?

---

### Post by ubix on 2011-05-11
Am I really the only one who lost address books, multi-lingual capabilities, and who is bothered by erroneous file handling messages when opening file folders and trash :o

Does anybody know if we can expect these things to be fixed soon?

---

### Post by shurkes on 2011-05-13
i agree wit you with part of the things you wrote.
i'm working with thunderbird and didn't lose any data.
the icon of skype that disappeared is very annoying.
i had to configure again the languages but its working fine with the three lang i need.

i might also downgrade but in this case it will be an upgrade.

cheers

---

### Post by YfoMp5QBh2 on 2011-05-13
I upgraded from 10.10 to 11.04 and had problems with LIRC.

Firstly the system seemed to repeat single keypresses on my remote twice. That was fixed quickly by adding some simple code through gedit,
Now LIRC doesn't work FULL STOP

Secondly, I was a bit thrown about where to go to turn off desktop effects (compiz desktop effects cause horizontal tearing in XBMC when playing a video). In 10.10 its just a right click on the desktop but in the case of 11.04 had to install the compiz-control-panel specially, and even then there didnt seem to be a 'turn compiz off' button unless I wanted to uninstall compiz completely.

I like using LIRC with XBMC and has worked 'out of the box' since 10.04, and because I couldnt be bothered fixing further faults or googling the answers in the forums, I downgraded back to 10.10

---

