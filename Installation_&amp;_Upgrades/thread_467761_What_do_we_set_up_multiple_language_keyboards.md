---
title: "What do we set up multiple language keyboards?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2007-06-08
Dear Ubuntufolk:

I have a need to type in more than one language.  This works fine in XP, but I have not been able to understand how to change keyboards in Ubuntu.  I have installed language support for the languages that interest me--all Western languages so there is no issue with ideograms and such--but I don't see how to change keyboards from one language to another.  I see that I have SCIM installed, but it doesn't seem to do anything.  When I try to use it to change keyboards using the hot-keys it lists nothing happens.  When I am occasionally typing and press ctrl space, I get another language--but only one--and I can get out of it by pressing ctrl space a second time.  Can anyone tell me how to set this up so I can easily change from keyboard to keyboard?

Thanks.

Whatawonderfulday

---

### Post by imon9 on 2007-06-08
if scim is not the default input method (by default, X-input is default) so you have to type this in terminal:
> im-switch -z en_US -s scim

if you intend to use SCIM with KDE/QT programs, like amarok, kopete, then u must install the qtimm-scim pakages, type this in the terminal:
> sudo apt-get install scim-qtimm

if u see the scim icon on the taskbar, right click and choose "SCIM setup' then u can configure it to the hot-keys you like...

under "frontend > global setup"
in XP, the hot-keys is Alt-Shift, so if u want, you can change SCIM to switch language by that too... also, 

under "IMEngine>global setup"
here, you can choose which input method to be available for u. If i'm not mistaken, ubuntu SCIM comes pre-configure with loads of language.. most that i never even used, so uncheck those u dont use.

btw, like me, i am using chinese and cyrilic keyboard, and it is not available from the list.. in such cases, go to "start>administation>preferences>language support" select the extra language support you wanted. after restart, the input method will be available in your SCIM setup list... choose whichever you like

hope this helps

---

### Post by Whatawonderfulday on 2007-06-08
Thanks, Imon9!

But there is some kind of problem.

First of all, language preferences is okay, I've installed language support for the languages I want.

However, the only time I can get the SCIM hot-keys to do anything is when I am doing a spell check on a Thunderbird letter I am composing.  Then it scrolls through a bunch of languages.  But nothing happens when I try to use it when I am actually composing a letter.  Ditto with open office.

What does happen is that if I hit ctl space, then I get Russian, and if I hit ctl space again I'm back to english.  But if I use hot keys with the up arrow, then I get some problems with the screen.  With other hot-keys I've defined I get all kinds of other hot-key interpretations unrelated to keyboard language (special types of delete, that sort of thing).

I should point out that I am under gnome.  If SCIM is for KDE, then kaput.

Otherwise, there's something I don't understand.

When I typed the code you gave me into the terminal, I tried it with en_us, but I really am standardizing to en_uk, so I finaly tried that.  I did do the get on the modules you said with the other code, even though I don't use the KDE stuff.

Is there any way to get the multiple keyboards up?


thanks very much.

Whatawonderfulday

---

### Post by imon9 on 2007-06-08
SCIM is for gnome so u can rest assure...though i am having an important final..so i cant reply you just yet... 

i think it is just some setting problem...will look into it later, ok?

---

### Post by Whatawonderfulday on 2007-06-08
Thanks IMON9.

I will wait for you to finish your exam.  May God bless your performance on it.

Whatawonderfulday

---

### Post by imon9 on 2007-06-09
just home :)

ok, here we go again... let me explain a little of the technical side of the whole "input" method in linux, ok?

so, now we are using ubuntu and using gnome-desktop... by default, all program uses X-input method which lack a bit of multiligual support (actually cyrilic is available)

anyway, like i said, if you wanted all program to start using "SCIM" as default input method, you have to do the following in terminal:
> im-switch -z en_US -s scim <---please comfirm that you have done this

secondly, IF you see the SCIM button on the tastbar, i assume that it is automatically start everytime you restart your computer... <----please comfirm this too

(anyway, if you don't see the icon in taskbar... use Alt-F2 and run "scim" ) 

next, put your mouse cursor to any text box (for example search bar of google in firefox" AND make sure that SCIM is "activated" , this can be done by typing the "hot-key' assign in SCIM setup to "turn on" ... after you turn it "ON", do not type the hotkey to turn it "OFF" again! 
(note; i can't remember the default hot-keys for this because i changed mine to "Ctrl+Alt+Return" ... hoever i suspected that yours is "ctrl-space" since you claimed that the language changes when you did that in certain occasion.

next, toggling between your language can be done by the "hot-key" of SCIM for "Next Input method" OR "Previous input method"

OR you can do it by left click on the SCIM icon in the tastbar <---- i suggest you do this because if everything is setup correctly, left-click on the icon will show you a list of available input method (language list) <--- please comfirm that a language list appears in your case

okay, now type something to comfirm if the language you selected is corresponding to what you want :) obviously, if all above have been comfirm to work correctly, at this point, the font of your selected will appear magically ;p

Please let me know at which point did you got stuck, ok?

btw, SCIM toggling btween input method/language "hot-key" can malfunction in certain cases. So, do feel free to change them into some-other hotkeys just to experiment with it...

also, regarding using SCIM in KDE programs, you will need to install extra pakages call scim-qtimm, by entering the command into terminal
> sudo apt-get install scim-qtimm

with this, comes the end of my detail tutorial.. feel free to ask any question now :)

oh yes, regarding you funny screen problem..can you be a bit more specific what kind of "funny" screen problem is that? screen chage color, got distorted? 

It is rather possible that the hot-keys you've set in the "scim" is over-lapped with some other programs..in such a case, i advice changing the SCIM hotkeys to something less "typical" ... hope all this will solve your problem once in for all

---

### Post by Whatawonderfulday on 2007-06-09
To IMON9:

Thanks very much.  Let's take things in order.

ubuntu 7.04; gnome desktop.

language support installed.


root@confused:/home/ubuntubeginner# im-switch -z en_US -s scim
No system wide default defined just for locale en_US .
Use "all_ALL" quasi-locale and set IM.
Using `/etc/X11/xinit/xinput.d/scim' to provide `xinput-all_ALL'.
root@confused:/home/ubuntubeginner# 

I don't understand this message.  I've run it with en_UK and I get the same message.  I believe that when Ubuntu installs it doesn't distinguish between en_US and en_UK, but wherever I can in the system, I have defaulted to en_UK, for example Thunderbird and OpenOffice.

I have on the bottom panel the SCIM logo in a little icon.  I have in the upper panel next to the firestarter icon and the Ubuntu upates available icon something that looks like a typewriter that also is for SCIM.  These icons have been there for ages.  I just don't know what to do with them

I have now opened SCIM global setting and changed the hot keys as follows:

Trigger:  Control+Alt+Shift+space

Turn On:  Control+Meta+N

Turn Off:  Control+Meta+F

Next Input Method:  Control+Meta+X

Previous Input Method:  Control+Meta+P

Show Input Method Menu:  Control+Meta+M

Note that I hold down ctl shift left alt and another letter, and the program interprets that as ctl+Meta+letter.  I don't know enough to know what Meta means.

Before we continue note that ctl+space giving Cyrillic must have been something to do with the X-Windows provision of Cyrillic, because I had never set up or tried to use SCIM when I was getting Cyrillic.

Here is a text window, is it not?

First I will turn on SCIM with the above key combo.

I have turned it on.

Now I will try to switch to next input method as above.

Here is what I get:  English.  Something's wrong.  I'll try again with trigger as above.

Here is what I get English again.

I will try after trigger, turn on.

Here is what I get: English.  Note that in the global box the language that is in the upper drop-down menu is set to Greek.  I don't know what I should have there.  I do want Greek.  Note also that I have unchecked embed and share, the two boxes below the drop-down language menu.  Note that I did click apply when I change the hot-keys.

I will now try next input method.

This is what I get.

Previous Input Method:

This is what I get.  Note that when I had the go up key used as part of this key combo what happened was that the displayed windows shrunk to about one third size for about a second and then returned to normal size.  That is the funny-screen behaviour that you asked me to explain.  With the current key combo that doesn't happen.

Now, show input menu:

Nothing happened.

Here's what happens with ctl space:

&#1082;&#1083;&#1076;&#1089;&#1092;;&#1081;&#1089;&#1072;&#1076;&#1092;;&#1083;&#1089;&#1072;&#1082;&#1092;&#1081;

&#1061;&#1077;&#1088;&#1077;'&#1089; &#1074;&#1093;&#1072;&#1090; &#1093;&#1072;&#1087;&#1087;&#1077;&#1085;&#1089; &#1074;&#1093;&#1077;--

well well well.  It stopped typing in Cyrillic Maybe SCIM has finally kicked in.  Let;s try again:

trigger.
turn on.
dfl;jk
next input method:
lsadkfj;  Still English.

previous input method.

still the same

menu:

dsfa;l  &#1073;&#1091;&#1090; &#1048; &#1093;&#1072;&#1078;&#1077; &#1081;&#1091;&#1089;&#1090; &#1090;&#1091;&#1088;&#1085;&#1077;&#1076; &#1090;&#1093;&#1077; &#1062;&#1099;&#1088;&#1080;&#1083;&#1083;&#1080;&#1094; &#1073;&#1072;&#1094;&#1082; &#1086;&#1085;, &#1091;&#1089;&#1080;&#1085;&#1075; &#1048; &#1090;&#1093;&#1080;&#1085;&#1082; &#1089;&#1090;&#1083; &#1063; &#1089;&#1087;&#1072;&#1094;&#1077;. &#1048; &#1090;&#1093;&#1080;&#1085;&#1082; &#1099;&#1086;&#1091; &#1074;&#1080;&#1083;&#1083; &#1073;&#1077; &#1072;&#1073;&#1083;&#1077; &#1090;&#1086; &#1091;&#1085;&#1076;&#1077;&#1088;&#1089;&#1090;&#1072;&#1085;&#1076; &#1074;&#1093;&#1072;&#1090; &#1048; &#1072;&#1084; &#1090;&#1099;&#1087;&#1080;&#1085;&#1075; &#1092;&#1088;&#1086;&#1084; &#1090;&#1088;&#1072;&#1085;&#1089;&#1083;&#1080;&#1090;&#1077;&#1088;&#1072;&#1090;&#1080;&#1086;&#1085; &#1072;&#1085;&#1076; &#1082;&#1085;&#1086;&#1074;&#1080;&#1085;&#1075; &#1074;&#1093;&#1077;&#1088;&#1077; &#1090;&#1093;&#1077; &#1082;&#1077;&#1099;&#1089; &#1072;&#1088;&#1077;.  &#1061;&#1077;&#1088;&#1077;'&#1089; &#1072;&#1092;&#1090;&#1077;&#1088; &#1094;&#1090;&#1083; &#1063; &#1089;&#1087;&#1072;&#1094;&#1077;:

We're back to English.  Maybe SCIM isn't working?

Well I don't know what to do next, except say thank you, please solve the problem and I hope your final went excellently.

I await your reply.

Whatawonderfulday

---

### Post by imon9 on 2007-06-09
ok...found your problem already :)

here is the problem: 
you system did not all you to set "system-wide" usage of SCIM, that is why, in the end, they prefer usage of X-input instead of SCIM...

in some text area (the one i'm sure of, is in "text editor"/gedit, when you right click on its text area, you will have a right-click menu. at the bottom if the menu, you will see "choose input method" and you can see which is chosen by default. <---- can you tell me which one is?

anyway, you can choose SCIM manual and start trying to use greek, and see if it works? <---comfirm this

and if it works in "text editor", continue experimenting it by testing all the hot-keys

####
appaerently, you should be right that the cyrilic belongs to x-input instead of SCIM

also, i want to say IF you did not manage to set the system-wide SCIM, you wont be able to use it fully... because not all text-area let you right click on it and let you choose your input method.... a good example is this one in firefox did not...

FINALLY, THE SOLUTION..or at least the posible one...
i saw you using "root" to type your command...why are you log-in as root in terminal?
can you use your normal "user" status to type the command? it should make a difference
...the correct reaction of the terminal is that, after you type the command in "user"mode, it wil just accept the command and go to the next line :)

to double check everything, use this command: 
> printenv
<---- please copy and paste the output here in the forum..

As comparison, i will include mine here (note: i ommited some irrelevent lines)
> DESKTOP_SESSION=default
QT_IM_MODULE=scim
GDM_XSERVER_LOCATION=local
XMODIFIERS=@im=SCIM
LANG=en_US.UTF-8
GDMSESSION=default
GTK_IM_MODULE=scim


---

### Post by Whatawonderfulday on 2007-06-10
Thanks IMON9.

I have to run right now, back in several hours, but here is what I've done.

In the text editor gedit 2.18.1, right clicking tells me that the input method is set to SCIM (!).

However, when I try to use the input method I don't get anywhere.

I next typed printenv (under root) and got just what you have, except that the langage is en_GB.  As I said everywhere I could I set the default to British English (I thought it was en_UK).  I doubt this is the problem.

Next, as for why I use root.  I have the options of using Konsole, Terminal and Terminal Program -- Sudo.  I just don't understand what the differences are.  If you could explain, I would be obliged.

Next, when I opened Konsole I got the following, and I think the problem is here.

confusedubuntuuser@lostinthewoods:~$ im-switch -z en_US -s scim
Please install following packages:
  "( scim-qtimm )" .
confusedubuntuuser@lostinthewoods:~$ sudo apt-get install scim-qtimm
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
scim-qtimm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
confusedubuntuuser@lostinthewoods:~$ im-switch -z en_US -s scim
Please install following packages:
  "( scim-qtimm )" .
confusedubuntuuser@lostinthewoods:~$

I'll be back in a few hours to continue.

Thanks very much.


Whatawonderfulday

---

### Post by imon9 on 2007-06-10
indeed it sounded peculiar that you already have scim used as main input, then the table should work as advertise :p

anyway, i wanna say something else... it seems you are able to set "greek" as your language but nothing turn out to be greek... ermm, just as a caution, did u check the "drop-down" list/expand the language selection list in SCIM setting to see if the "greek" input is greek and not "greek-english" (just to be on the save side..since i dont use greek, i wont know if there is such thing)

---

### Post by Whatawonderfulday on 2007-06-10
Dear IMON9:

I'm not sure just precisely where you mean I should look, but SCIM input > Font End > Global Setup > drop down menu 'keyboard' has the keyboard set to Greek.  IMEngine > Global Setup has English and Russian checked.   None of the other languages listed are useful--as you yourself remarked.   I don't understand any of the other check boxes, and the settings possibly have been disturbed.

I wonder if the problem doesn't have something to do with the installation?  I wonder if I shouldn't uninstall both SCIM and qtimm and reinstall? How should I do the uninstall and reinstall?     In which order (i.e. first SCIM and then qtimm, or the opposite)?   Under Konsole?  Terminal -- Sudo?   I don't know.  As far as I can see the installation of SCIM is faulty.

Another possibility is that there is a conflict with some other package.  The only ones I've been installing and reinstalling have to do with FAX services.  I don't even remember which ones are installed right now.

Thanks for your help.

Whatawonderfulday

---

### Post by imon9 on 2007-06-10
well, it is possible... i am going to suggest your to un-install SCIM and SCIM-QTIMM as well...

i am not very possitive of the "terminal" way to do it, because i can teach you how to "unintall" but i can't remember how to "purge" the setting... coz usually, i would use "synaptic"

so i suggest you use synaptip as well..

run synaptic, find scim and scim-qtimm, uninstall them completely (with the setting)... (if in anyway you did not delete the setting, you will find something listed in "residue setting" .. so you can uninstall those too)

then reinstall by using synaptic should be as easy as click and choose!

go on and try it..!

---

### Post by Whatawonderfulday on 2007-06-11
Dear IMON9:

We seem to have made a lot of progress.  Let's see where we are:

&#913;&#957; &#964;&#965;&#967;&#972;&#957; &#958;&#941;&#961;&#949;&#953;&#962; &#917;&#955;&#955;&#951;&#957;&#954;&#940;, &#954;&#945;&#964;&#945;&#955;&#945;&#946;&#945;&#943;&#957;&#949;&#953;&#962; &#972;&#964;&#953; &#945;&#965;&#964;&#972; &#948;&#959;&#965;&#955;&#949;&#973;&#949;&#953;.

&#1048; &#1076;&#1086;&#1085;&#1090; &#1082;&#1085;&#1086;&#1074; &#1056;&#1091;&#1089;&#1089;&#1080;&#1072;&#1085;.

I did this with the SCIM taskbar that comes up, not the hot keys.

Here's with the hot-keys:

flkjl;kdflk;s

d;lkflaksdfj;lkksljf;lksjf;lksdals;kdjf;laskjdfas;fk;lsadkjf;lksjdf;lk

As far as I can see the hotkeys don't work.

I didn't use the hot-keys in Windows, so I can live with just the taskbar, but it would be nice to get things set up properly, if you know what to do.

I see that the typewriter I am using is 'English/European'.  What I don't know is how to switch it to French say.  I don't have that listed anywhere.  Do you know what to do?

Also, the taskbar sticks out onto the lower panel.  How do I arrange it to bother something else?

Also, for anyone who is consulting this, when I reinstalled SCIM and qtimm, I also installed some other libraries I figured out just by scanning the Synaptic output on a SCIM search.  They were the libraries that seemed to have something to do with extended language use.  Before I installed the extra libraries, I didn't have all the languages I wanted.

Awaiting your reply--

Whatawonderfulday

---

### Post by imon9 on 2007-06-11
hi,

i'm glad to hear that things finally somewhat workout fine for u...

regarding the hotkeys error, i would like to say that, in anyway, you can try changing it to somthing else then "apply & reload setting'  or better log-out and log-back into ubuntu and start testing it again.. sometimes, it correct itself (maybe the original setting is not registered correctly while being set/install

about the french input thing..i'm sure you can add it at: start > system > administration> language support and add "french" support

afterwards, you will find the input method in your SCIM input list.

regarding the taskbar stick out? i am a bit unsure what you mean by this, perhaps a screenshot will helps :) but i am fairly sure you can configure them under scim icon right-click >settning > panel > GTK ...

play around with the configuration to get it to your liking :)

anything, just post here.. i check my thread at least twice a day lately

---

### Post by mitivic on 2007-06-12
Thanks to sir imon9!

I was trying to enable both Chinese and Japanese input
 in English locale.

The command did work!
Though I alter it to "en" trying to apply it on all English locale?

 im-switch -z en -s scim

However, there is some wired behavior when I use scim...
Both in Chinese & Japanese locale...

---

### Post by Whatawonderfulday on 2007-06-13
To IMON9:

Thanks very much for your help.

For the taskbar issue, I found how to get it to snap back to the margin by itself, so there is no longer any problem.  I find the whole SCIM layout confusing, so I don't even really know what I did to get the taskbar to snap back automatically.

With regard to the French thing, I already have French installed in language support.  You can assume that any language I write about here, unless I say otherwise, the language support is installed on the system.  However, the French language just doesn't come up on the list.  I see that the English keyboard is actually listed as English/European, so I suspect that it is used for all the Western European languages.  But that doesn't explain where the special characters are--all of these languages have special characters compared to English.  I did see that there was a special keyboard with Latin pre and post, which I take means that you type the accent or whatever either before or after the letter.  Maybe that is how the special characters are entered, I don't know.  If so, it seems a very cumbersome method for continual typing in a foreign language.

As for the hot-keys, I have been very busy and have not yet had the time to experiment to see what can be done with them.  That is also why there has been a delay in my replying.

Whatawonderfulday

---

### Post by imon9 on 2007-06-13
to mtivi,

can u explain in more detail context what is the "strage" behaviour"?

to Whatawonderfulday,

i did a bit of search for French input since i do not use them myself. It appears there is no specific keyboard layout in SCIM for french. HOWEVER, i did have a useful solution for you.

Go to System -> Preferences -> Keyboard > "Layout Options" tab. 
Expand the options for "Compose Key Position" and Choose a key you don't use for much, and set it as your Compose key! (I use my left WINDOWS key)

To enter french character not available in english keyboard setting, do the following:
hold the "Compose key" down and then type in the characters you want to mash together. For example, you can make an ñ by typing <compose>+n+~, or è by typing <compose>+e+`, or ß by typing <compose>+s+s and voila your letters appear.

i am not sure what else is there. but you could experiment with it i suppose. :D hope this helps you a bit

---

### Post by imon9 on 2007-06-14
to whatawonderfuday,

i found out what's the problme with the shortcut and why you cant switch with hotkeys...
here's the thing: somehow the SCIM is not responding to any hot keys involving "alt" keys.. so please set a hotkeys not involving "alt" and try it out.

however, i do not know why such behaviour with SCIM. will let you know soon after i'm free enough to investige.

do let me know if it works when you don't use "alt" keys... cheers :)

and For all the thanks for you folks..you are always welcome... :) ubuntu will always be a warm community

---

### Post by imon9 on 2007-06-15
hi,

i just found out why the "alt" can't be used!! it is locked by a setting which serve as the hotkeys for moving for windows. Disable that setting and you will be good to go! (sorry, today i just moved to xfce instead of gnome, so i can't give you the step by step instruction.

---

### Post by avik on 2007-06-15
> i just found out why the "alt" can't be used!! it is locked by a setting which serve as the hotkeys for moving for windows. Disable that setting and you will be good to go! (sorry, today i just moved to xfce instead of gnome, so i can't give you the step by step instruction.

In case anyone is wondering, that setting is under System->Preferences->Windows.

---

### Post by mitivic on 2007-06-16
To imon9:

I installed both Chinese and Japanese language surpport
When I'm using scim I offten get to a situation that
input get interrupt by it self?!
It's like when I want to input some character pressing "wu06"
it should have show some character at the end.
BUT the "6" wash out former input so I get only "6" in a progressing input.

This problem?! occurs whether I set locale to en, ch, or jp ~

sometimes scim shows duplicated keyboard tray icon
but I don't know if it means that the problem is due to duplicated scim prossess?!
Maybe I should check system monitor when it happens /_\

Thanks for asking :D

---

### Post by imon9 on 2007-06-16
hi mitivi,

i use chinese input as well, but i use the "smart pinyin" so i'm not sure what is the problem with you input? which input method are u using?

btw, usually the combination choice should able to show on a extra list, and not only at the area you type, isnt it?

about the duplicate tray icon, it is a known thing, ot a bug... it appear whenever you open some program with "root" for example, synaptics... this is actually means 1 is for user and 1 is for root, it does not interfere with the function of SCIM.

if you feel bothered with that, you can hide the "root" SCIM icon by setting to to "hide"/do not show in tray :)

let me know more about the input method.. a screen shot whould be nice

---

### Post by Whatawonderfulday on 2007-06-18
To IMON9:

Thanks very much.  I have got the hot-keys to work: I have made the alt key change in preferences for Windows, which function I never use anyway, and I have also for good measure changed the hot-key assignments. 

&#919;&#949;&#961;&#949;'&#963; &#945;&#957; &#949;&#967;&#945;&#956;&#960;&#955;&#949; &#959;&#966; &#964;&#951;&#949; &#952;&#963;&#949; &#959;&#966; &#951;&#959;&#964;&#954;&#949;&#965;&#963;.  &#921;&#964;&#963; &#955;&#959;&#965;&#963;&#965; &#915;&#961;&#949;&#949;&#954;, &#946;&#965;&#964; &#953;&#964;&#963; &#915;&#961;&#949;&#949;&#954;.  &#913;&#957; &#952;&#941;&#955;&#959;&#965;&#956;&#949; &#957;&#945; &#956;&#953;&#955;&#940;&#956;&#949; &#955;&#943;&#947;&#959; &#963;&#964;&#945; &#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;, &#949;&#943;&#957;&#945;&#953; &#949;&#957;&#964;&#940;&#958;&#949;&#953;.  &#1061;&#1077;&#1088;&#1077;'&#1089; &#1090;&#1093;&#1077; &#1089;&#1072;&#1084;&#1077; &#1090;&#1093;&#1080;&#1085;&#1075; &#1080;&#1085; &#1056;&#1091;&#1089;&#1089;&#1080;&#1072;&#1085; &#1082;&#1077;&#1099;&#1073;&#1086;&#1072;&#1088;&#1076;.  &#1053;&#1077;&#1077;&#1076;&#1083;&#1077;&#1089; &#1090;&#1086; &#1089;&#1072;&#1099; &#1099;&#1086;&#1091; &#1093;&#1072;&#1078;&#1077; &#1090;&#1086; &#1073;&#1077; &#1094;&#1083;&#1077;&#1078;&#1077;&#1088;, &#1074;&#1093;&#1080;&#1094;&#1093; &#1099;&#1086;&#1091; &#1089;&#1077;&#1077;&#1084; &#1090;&#1086; &#1073;&#1077;, &#1090;&#1086; &#1076;&#1077;&#1082;&#1086;&#1076;&#1077; &#1090;&#1093;&#1080;&#1089; &#1090;&#1099;&#1087;&#1080;&#1085;&#1075;.

One question I have is how to use the latn-post and latin-pre keyboards, since they clearing are going to provide all the extra characters.

Another question I have is what is the difference between 'trigger' and ón'.

Well! I have just found how to type an acute accent in French.  I'm on Latn-pre and this gives a letter I need á: I type quotation mark followed by the letter.  Here's e:  é Here's o: ó And so on.  Here's a good character ô:  Accent circumflex.  Upper case 6 followed by the letter that need's its hat.

 So I seem to have solved part of the problem.

If I don't reply quickly, I'm just busy.

Whatawonderfulday

---

### Post by ikman on 2007-06-22
I have been following your thread on your SCIM language problem. I have the Russian, Arabic, and 20 other languages after running several of the sudo commands like 'install scim-qtimm' and can Ctl+Space to open the taskbar list of languages, but Greek is no there. I used System -> Administration -> Language support to add Greek. 

But in System ->Preferences -> SCI Input Method Setup there is no 'Greek' listed in the IM Engine GLobal Setup menu (which has the exact list as the SCIM taskbar). I could go to IM Engine -> Generic Table and install 'Greek' but I have no idea how to do so. 

Is that what you did to get greek visible on the SCIM taskbar list?

Thank you.

---

### Post by Whatawonderfulday on 2007-06-23
To Ikman:

Let's see if I can remember what I did.  It can't be very difficult, because I'm not a Linux expert.

First, of all, System > Administration > Language Support. Install Greek.  From what you say, you've done that.

Next, System > Administration > Synaptic Package Manager > Search on SCIM.  I have the following installed:

im-switch

libscim8c2a

scim

scim-gtk2-immodule

scim-m17n

scim-modules-socket

scim-modules-table

scim-qtimm

scim-tables-additional

If you don't have one or more of these modules installed, then install it or them.  I think you should then find that Greek is supported.  I find SCIM a little confusing, but if you open the SCIM input method setup and go through all the various drop-down screens and fiddle you should eventually come up with Greek.  If you do all of the above and still have a problem, let me know and I will search a little harder.

Whatawonderfulday

---

### Post by ikman on 2007-06-23
Thank you. The key package for me was the scim-m17n. I am setting up several computers manually (for the experience) and on a subsequent setup I only updated the System > Administration > Language Support and installed the scim-m17n. The other packages were either installed automatically, or weren't really necessary.

You complete list is great to have for completeness, however.

Thanks for the response.

---

### Post by Whatawonderfulday on 2007-06-23
To Ikman:

Glad to help.  I was pretty sure that m17 was the module that supported Greek, but I am in a complete fog.  The writer/maintainers of SCIM should consider writing a 'setting up keyboards for dummies' chapter in Ubuntu guide.  What are you going to do with 20+ languages?  Are you a polyglot?

With best wishes--

Whatawonderfulday

---

### Post by single29 on 2008-07-13
[QUOTE=imon9;2814951]ok...found your problem already :)

FINALLY, THE SOLUTION..or at least the posible one...
i saw you using "root" to type your command...why are you log-in as root in terminal?
can you use your normal "user" status to type the command? it should make a difference
...the correct reaction of the terminal is that, after you type the command in "user"mode, it wil just accept the command and go to the next line :)

How can I use scim when I login as root? I can type Chinese as a normal user. thanks,

---

