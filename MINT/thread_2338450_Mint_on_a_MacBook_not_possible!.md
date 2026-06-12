---
title: "Mint on a MacBook not possible?!"
date: 2016-09-28
forum: MINT
---

### Post by frank-nord on 2016-09-28
Hi there,

im glad because i get my old MacBook (1.1 first gen) running again. [IMG]https://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG] 
Now i installed Leopard on it and want for multiple purposes Ubuntu or Linux Mint as a second bootable OS on it. 
I asked a friend how to do this and he told me to use Refind/Refit and install a 32bit Version of my Linux. But when i try to install in the Bootmenu, i only get a "legacy boot Device". My Friend told me that i would need a 32bit Bootloader because that Computer is pretty old and just supports that. 
in the Main Menu of the Image should be EFI/BOOT/bootia32.efi, but i can't find that.
Can someone please tell me if there is a trick or a workaround to get that solved?

I also found the Thread here: [https://ubuntuforums.org/showthread.php?t=995704](https://ubuntuforums.org/showthread.php?t=995704)
But I've endet up with the error: file not found.

I looked up for that to but did not find anything else and don't know what i does wrong or what i should do else.


Thanks and best wishes

---

### Post by howefield on 2016-09-28
Thread [s]moved to the "*Apple Hardware Users*" forum[/s] and on to the "*MINT*" sub forum.

---

### Post by apple-apple on 2016-09-28
I'm thinking that you may need to try a Ppc version of Ubuntu. Lubuntu and Ubuntu mate both support ppc I believe.

---

### Post by frank-nord on 2016-09-28
Ok, could you tell me why? Because it's a intel mac and I don't get the link why to go to ppc.

---

### Post by apple-apple on 2016-09-28
Sorry, I made a mistake. I got the models mixed up in my head.

---

### Post by kevow on 2016-09-30
I don't think you actually need refind to do a dual boot with Linux. I think that the default option key loader built in will be able to see the second os as a windows boot if you set it up to boot in legacy mode.

Also for refind you may have to reinstall it after loading Ubuntu. For me, the last couple of times I've tried loading it with multiple OSs the bootloader install messes up refind so I boot the recovery partition and run the install script again and that brings it back.

---

### Post by frank-nord on 2016-10-01
Well i installed it already, or better said i had help by a real nice guy who helped me out. 
Erfind still works but the keyboard is messed up.
The last thing is now that i don't can use the alt key and so don't get (im writing on my iMac :) ) ¡&#8220;¶¢[|{}&#8800; and so on. But i need that in Terminal and don´t find anything that helps by searching in the internet.


Do you have a hint for that to?

---

### Post by &amp;KyT$0P# on 2016-10-01
> **frank-nord said:**
> the keyboard is messed up.
The last thing is now that i don't can use the alt key and so don't get (im writing on my iMac :) ) ¡&#8220;¶¢[|{}&#8800; and so on. But i need that in Terminal and don´t find anything that helps by searching in the internet.


Do you have a hint for that to?
You've got a en-US keyboard layout, don't you?  Set keyboard layout variant to English (Macintosh), then use the right alt key.

---

### Post by frank-nord on 2016-10-01
sorry, no a german (qwertz) and don't have a right alt key, just left :(

---

### Post by &amp;KyT$0P# on 2016-10-01
Wait, shouldn't that layout have an AltGr key on the right?

Can you use German (Macintosh) layout variant?

---

### Post by frank-nord on 2016-10-01
I don´t have even on the big keyboard on my iMac a altgr.
I tried to use all appearing Mac-Keyboard options.
No, and nothing worked for me.

---

### Post by &amp;KyT$0P# on 2016-10-01
What Ubuntu version and flavor are you using?

Check the [FONT=Courier New]lv3:[/FONT] entries in [FONT=Courier New]/usr/share/X11/xkb/rules/evdev.lst[/FONT] for different ways you can move the AltGr key elsewhere.

---

### Post by frank-nord on 2016-10-01
Im using Linux Mint (afaik the sister of Ubuntu)
> **halogen2 said:**
> 

Check the [FONT=Courier New]lv3:[/FONT] entries in [FONT=Courier New]/usr/share/X11/xkb/rules/evdev.lst[/FONT] for different ways you can move the AltGr key elsewhere.
Im pretty new to Linux, so please explain me what means > lv3:?

---

### Post by &amp;KyT$0P# on 2016-10-01
> **frank-nord said:**
> Im using Linux Mint (afaik the sister of Ubuntu)
What desktop environment are you using?

> Im pretty new to Linux, so please explain me what means ?
[FONT=Courier New]lv3:[/FONT] is just a string in that file to look for.  It means level 3 shift, in otherwords, AltGr.
It prefixes the keyboard layout options you would be interested in.  Read through the list and please let us know which option you would like.

---

### Post by frank-nord on 2016-10-01
> **halogen2 said:**
> What desktop environment are you using?
It&#347; the Xfce, because i did'nt knew if any other would run smooth on the old Macbook.

In that File you told me, are a couple lines with lv3:, but honestly does'nt say that much to me.
Right now, neather the fn, ctrl nor the alt key seem to have any function. At best i would like to have it as it is/was on Mac OS. For example, alt + 8 means a brace, on 7 a pipe and so on.
Maybe the Apple key instead of getting the startmenue up, more shortcuts to work with, like apple + xcv (cut/copy/paste).
And maybe change the <> key with the ^° key. But i don't get how to do that with the options in that File.

There it says:

>   lv3                  Key to choose 3rd level
  lv3:switch           Right Ctrl
  lv3:menu_switch      Menu
  lv3:win_switch       Any Win key
  lv3:lwin_switch      Left Win
  lv3:rwin_switch      Right Win
  lv3:alt_switch       Any Alt key
  lv3:lalt_switch      Left Alt
  lv3:ralt_switch      Right Alt
  lv3:ralt_switch_multikey Right Alt, Shift+Right Alt key is Compose
  lv3:ralt_alt         Right Alt key never chooses 3rd level
  lv3:enter_switch     Enter on keypad
  lv3:caps_switch      Caps Lock
  lv3:bksl_switch      Backslash
  lv3:lsgt_switch      &lt;Less/Greater&gt;
  lv3:caps_switch_latch Caps Lock chooses 3rd level, acts as onetime lock when pressed together with another 3rd-level-chooser
  lv3:bksl_switch_latch Backslash chooses 3rd level, acts as onetime lock when pressed together with another 3rd-level-chooser
  lv3:lsgt_switch_latch &lt;Less/Greater&gt; chooses 3rd level, acts as onetime lock when pressed together with another 3rd-level-chooser
Could you please tell me how to do that?

---

### Post by &amp;KyT$0P# on 2016-10-01
In XFCE you can run this command in a Terminal to map the AltGr key on the left alt key -
```
setxkbmap -option lv3:lalt_switch
```

This command should reset -
```
setxkbmap -option
```

Refer to [FONT=Courier New]man setxkbmap[/FONT] for more info


EDIT I believe that might not "stick" though, as in, back to reset after a logout or shutdown.  But let's get it working for you first, before getting into automatically running it.

---

### Post by frank-nord on 2016-10-01
You'r great! Thank you!
 It works now not all good, but the really necessary keys are there.
Here is my alt + number key output:
¡²³¼[]|{}}

Im pretty sure that it sounds lazy, but im really a newbie, so i write "[FONT=Courier New]man setxkbmap" in the Terminal, but the output don't let me really know how i can config the other keys as i need them. Is somewhere a tutorial or something? Or could you describe me that?[/FONT]

---

### Post by &amp;KyT$0P# on 2016-10-01
You're welcome. :)

What other key configuration are you looking to do?

---

### Post by frank-nord on 2016-10-01
Great! :) 

[COLOR=#000000]The Apple key triggers the startmenue up (i really never need that i guess), [/COLOR][COLOR=#000000]instead of that i would like [/COLOR][COLOR=#000000]more getting the shortcuts to work with, for example like apple + xcv (cut/copy/paste). (as ist is on Mac OS)[/COLOR]
[COLOR=#000000]And maybe change the <> key with the ^° key. [/COLOR]

---

### Post by &amp;KyT$0P# on 2016-10-01
> **frank-nord said:**
> Great! :) 

[COLOR=#000000]The Apple key triggers the startmenue up (i really never need that i guess), [/COLOR][COLOR=#000000]instead of that i would like [/COLOR][COLOR=#000000]more getting the shortcuts to work with, for example like apple + xcv (cut/copy/paste). (as ist is on Mac OS)[/COLOR]
Does the file with the lv3: entries also have this entry?
```
altwin:ctrl_win      Ctrl is mapped to Win keys (and the usual Ctrl keys)
```

If so, try it -
```
setxkbmap -option altwin:ctrl_win
```

---

### Post by frank-nord on 2016-10-02
> **halogen2 said:**
> Does the file with the lv3: entries also have this entry?
```
altwin:ctrl_win      Ctrl is mapped to Win keys (and the usual Ctrl keys)
```
]

I can't discover that in the file. I see win key left and right, but not exactly like you told me to look up.

Here is what is in the file:

  lv3                  Key to choose 3rd level
  lv3:switch           Right Ctrl
  lv3:menu_switch      Menu
  lv3:win_switch       Any Win key
  lv3:lwin_switch      Left Win
  lv3:rwin_switch      Right Win
  lv3:alt_switch       Any Alt key
  lv3:lalt_switch      Left Alt
  lv3:ralt_switch      Right Alt
  lv3:ralt_switch_multikey Right Alt, Shift+Right Alt key is Compose
  lv3:ralt_alt         Right Alt key never chooses 3rd level
  lv3:enter_switch     Enter on keypad
  lv3:caps_switch      Caps Lock
  lv3:bksl_switch      Backslash
  lv3:lsgt_switch      &lt;Less/Greater&gt;
  lv3:caps_switch_latch Caps Lock chooses 3rd level, acts as onetime lock when pressed together with another 3rd-level-chooser
  lv3:bksl_switch_latch Backslash chooses 3rd level, acts as onetime lock when pressed together with another 3rd-level-chooser
  lv3:lsgt_switch_latch &lt;Less/Greater&gt; chooses 3rd level, acts as onetime lock when pressed together with another 3rd-level-chooser

and no!!! As i recognize current, the alt setting is after the restart gone :(

---

### Post by &amp;KyT$0P# on 2016-10-02
> **frank-nord said:**
> I can't discover that in the file. I see win key left and right, but not exactly like you told me to look up.

Here is what is in the file:

This line is **not** prefixed by [FONT=Courier New]lv3:[/FONT], it is exactly as written.

> and no!!! As i recognize current, the alt setting is after the restart gone :( 
Right, that's expected at this point.  Just re-run the setxkbmap command.
Once we figure out all the xkb options you like, then we'll set it to automatically run.

---

### Post by frank-nord on 2016-10-02
Oh ups&#8230; yes, now i found it. :eek:

I set in Terminal the Command you told me. Now the ctrl key does xcv (more functions i didn't found yet) but the Apple key have now no more function as it seems.
Should it be that way?

---

### Post by &amp;KyT$0P# on 2016-10-02
Maybe you need to combine in one setxkbmap command?

(Clear existing options first, see above on how to do that.)

```
setxkbmap -option altwin:ctrl_win -option lv3:lalt_switch
```

---

### Post by frank-nord on 2016-10-02
> **halogen2 said:**
> Maybe you need to combine in one setxkbmap command?

No, it stays the way as it described before. ctrl key holds the functions, apple key does nothing. :(

---

### Post by &amp;KyT$0P# on 2016-10-02
Then what is the apple key?  I don't have one on my Mac, so I assumed you meant command key &#8984; given your description -
> The Apple key triggers the startmenue up (i really never need that i guess), instead of that i would like more getting the shortcuts to work with, for example like apple + xcv (cut/copy/paste). (as ist is on Mac OS)

---

### Post by frank-nord on 2016-10-02
jup, exactly that´s the key i meant to! But that what is working now is the left from alt, ctrl. i have ctrl, alt and then apple/command key and thats the one i want to work (like under OS X)

---

### Post by &amp;KyT$0P# on 2016-10-02
It works for me, in Xubuntu 16.04, with German (Macintosh, eliminate dead keys) keyboard layout.

Let's look at the key codes from your keyboard, by [this method]("https://ubuntuforums.org/showthread.php?t=2335394&p=13538113&viewfull=1#post13538113").  When the command is running, press only the command key, then wait 10 seconds.  This is what I get -
```
$ sudo showkey -s
kb mode was ?UNKNOWN?
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
0x9c 
0xe0 0x5b 0xe0 0xdb 

```
Please post your output here.

---

### Post by frank-nord on 2016-10-02
ok, done that.

here it is:

```
~ % sudo showkey -s
kb mode was ?UNKNOWN?
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
0x9c 
0xe0 0x5b 0xe0 0xdb 


```
looks pretty similar to me

---

### Post by &amp;KyT$0P# on 2016-10-02
Yep, that's exactly the same.

In Settings > Keyboard > Layout , is "Use system defaults" checked?  If so, un-check it and re-run the setxkbmap command if needed.

Does Mint have their own keyboard layout handler that maybe interfering?

Aside that, I'm out of ideas on this one, sorry.

---

### Post by frank-nord on 2016-10-02
Nope, there i tried (by myself, before i asked here to solve it) to set it. I unchecked "Use system defaults" and set the Keyborad Model to Macbook/Macbook Pro (intl), under that is Keyboard Layout, that i set to "German/ German (Macintosh)".
I thought when we work with Terminal, we would override that.
Should i change some of that/disable some?

---

### Post by &amp;KyT$0P# on 2016-10-02
Here's the xfce keyboard settings I'm using for testing this -

[[img]https://s19.postimg.org/cp28ofxnj/Screen_shot_2016_10_02_2.png[/img]](https://postimg.org/image/cp28ofxnj/) (click to enlarge)

---

### Post by frank-nord on 2016-10-02
yeah, thats waht i also found when i googled my problem before. But in my list is no "eliminate dead keys" that i could choose. Does i need to download/set there something before or should it be in by default?

---

### Post by &amp;KyT$0P# on 2016-10-02
It was "just there" for me.  I didn't do anything specific to get it.

---

### Post by frank-nord on 2016-10-02
ok found it now to, changed it, tried the "setxkbmap -option altwin:ctrl_win -option lv3:lalt_switch" again, no change... :(

---

