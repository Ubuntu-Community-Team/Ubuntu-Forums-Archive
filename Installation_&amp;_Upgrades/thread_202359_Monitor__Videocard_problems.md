---
title: "Monitor / Videocard problems"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by thaive on 2006-06-23
Greetings, i'm still new to ubuntu but i seem to be having a problem i can't really fix myself.

When i try to run games like chromium the menu is slow as and feels like its struggling,  whne i try programs like stellarium and supertux my monitor chicks a hissy and everything is shrunt and stretched multiply times over on   diagnol on the screen.

any suggestions on how to fix this? i ran easyubuntu and installed nvidia and ati drivers so i'm not sure what else to do.

cheers
thaive

edit - my videocard is a raedon 9250, and i tried runnig the auto script on [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

but it doesn't detect my card ....

---

### Post by zxee on 2006-06-23
IMO ati video cards are not as well supported in linux. If you can't get 3D accelleration enabled some feature rich games are going to be slow or cause problems with the screen. You can run the video set up script. but before you do that I recommend that you have available all your system info, at least keyboard, mouse, monitor, video,  written down. The command, typed in a shell. is > dpkg-reconfigure xserver-xorg

---

### Post by thaive on 2006-06-23
ok so i did all that again, but still i get zip,

i type in 
$ lspci

and got alot of information spewed out, interstingly one was this:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

but i have a raedon 9250 so i'm confused as to why it thinks its a 9200 pro

---

