---
title: "Keyboard Shortcuts Errors After Dist-Upgrade"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by nibirumarduk on 2008-10-29
Hi guys. I just upgraded from Hardy to Intrepid. I'm running into some very annoying issues. Specifically speaking, I'm no longer able to use any of my Up, Down, Left and Right arrows in any of my apps like I used to.

Some practical example are: Prior to the dist-upgrade, depressing either the Up or Down arrow keys in Epiphany browser would have allowed me to scroll up or down a webpage, but not now. And pressing the the Up arrow key, does not bring up the last command I typed in GNOME terminal like it used to before the upgrade. Similarly, my Insert, Delete, Home, End keys do not work anymore. 

I cannot also press Ctrl C and Ctrl V for any cut & paste operations like before. Also I while I have a Generic 105 key keyboard, under System > Preferences > Keyboard > Layouts, Intrepid thinks I have a Generic 101 key PC instead. 

How do I rectify these? Can anyone help me out here? Please?

---

### Post by nibirumarduk on 2008-10-30
Tried to perform a "sudo dpkg-reconfigure console-common". Found that console-common wasn't installed for whatever reasons. Went ahead and installed that, everything went smoothly till the "sudo dpkg-reconfigure console-common" portion.

I forgot that as my arrow keys aren't working anymore, I could not select any of the options brought up in the debconf dialog. The only choice was to stick with the default i.e. "do not touch my keymaps" or something. :(

Is there a config file or 2 that I can manually edit (e.g. while in failsafe) perhaps where I can define my keyboard type (seems like the new xorg doesn't read the xorg.conf anymore and insists on recognizing my keyboard as a 101 key one instead of it being a 105 generic) as well as set the default behavior of like my Left, Right, Up, Down, Page Up, Page Down, Insert, Delete, Home, End, etc keys? If there is/are, how do I go about it i.e. what stuff do I need to add/remove, comment or uncomment?

---

### Post by 080801jk on 2008-10-30
&#30005;&#21147;&#20445;&#38556; &#12288;&#12288;&#25968;&#25454;&#20013;&#24515;&#26426;&#25151;&#37319;&#29992;&#21452;&#36335;&#39640;&#21387;&#20379;&#30005;&#65292;[**google&#20248;&#21270;**](http://www.jingke.org/)&#20379;&#30005;&#23481;&#37327;&#20026;1200KVA&#12290;&#21452;&#36335;&#20887;&#20313;(1+1)UPS&#30005;&#28304;&#12289;[**&#32593;&#31449;&#20248;&#21270;**](http://www.jingke.org/)&#36229;&#22823;&#21151;&#29575;&#30340;&#26612;&#27833;&#21457;&#30005;&#26426;&#32452;&#25552;&#20379;&#21487;&#38752;&#30340;&#21518;&#22791;&#20379;&#30005;&#33021;&#21147;&#65292;[**&#34394;&#25311;&#20027;&#26426;**](http://www.jingke.org/xunizhuji.htm) &#20174;&#32780;&#20445;&#38556;&#20805;&#36275;&#12289;&#25345;&#32493;&#30340;&#30005;&#21147;&#20379;&#24212;&#65292;[**&#32593;&#31449;&#20248;&#21270;**](http://www.jingke.org/wangzhanyouhua.htm)&#20445;&#35777;99.99%&#20197;&#19978;&#30340;&#25345;&#32493;&#20379;&#30005;&#29575;&#12290;[**&#32593;&#31449;&#20248;&#21270;**](http://www.jingke.org/wangzhanyouhua.htm)&#26426;&#25151;&#21508;&#29420;&#31435;&#21306;&#22495;&#22343;&#25552;&#20379;&#20027;&#22791;&#21452;&#36335;&#30005;&#28304;

---

### Post by Jovaro on 2008-10-30
I am having the same issue. My keyboard works just fine without X. Try to switch to a different tty (ctrl-alt-F1/F2/F3 etc) and login there.

edit: I just found my problem. There was a Xmodmap file in my home directory that was being used. Deleting this fixed all non-functional keys.

---

### Post by nibirumarduk on 2008-10-30
> **Jovaro said:**
> I am having the same issue. My keyboard works just fine without X. Try to switch to a different tty (ctrl-alt-F1/F2/F3 etc) and login there.

edit: I just found my problem. There was a Xmodmap file in my home directory that was being used. Deleting this fixed all non-functional keys.

Hi Jovaro. Many thanks for responding. Sorry to hear that you seem to be having almost the very issues at least for a while.  Glad that your troubles are now history. :)

I did try switching ttys as you have suggested. All my keys work fine there e.g. tty2. However when I switched back, they don't. :confused: Tried looking for any Xmodmap files that I may have in my /home but there was none. So no go there. :( Guess I'm left with but no other options but to do a fresh install. Thank heavens I kept my /home on a separate partition. ;) 

I suppose installing afresh at each and every new major release time ain't too tedious although I still can't figure out what went wrong. Didn't experience any unseeming incidents during the Gutsy to Hardy dist-upgrade and was expecting none this time around either. But alas, it was not to be. :(

---

