---
title: "Simplify Input/IME Language"
date: 2009-06-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gizenshya on 2009-06-27
A while back I tried going through options to install Japanese input in my English 9.04 box (without changing the box to Japanese).  After going through the menus and failing, I went back to windows to do my Japanese typing.

Earlier today I decided to google it and find out how (in 9.04).  Well, I finally found a tutorial that works ([Link](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM)), and it is a very long and drawn-out process.  The tutorial itself took time to find, as I found more and more keywords from failed search attempts for hours before narrowing it down enough.

The issues it lists are precisely what I'm talking about:

> There are two main issues here:

1.Installing the SCIM input system that will work in a locale other than converting your whole install to Japanese, i.e. you want Japanese input in an English login.

2.The fonts look initially terrible. Therefore a certain amount of customisation [sic] is required to make all the Kanji's render in the same style and Hiragana & Katakana to render in a matching style. 

Can something like what that tutorial does be added to the options in a later distro?  Lots of stuff similar to this is, but for some reason it always assumes you want to change your computer's global language instead of just adding a simple input language.  It took me over an hour to do.. there must be a simpler way.

Thank you

---

### Post by portis on 2009-06-27
ibus is better than scim. Fedora has adopted ibus as the default input method framework. I can input chinese characters under en_US locale with ibus. You can simply install ibus and corresponding input methods, and do a im-switch -c, and choose ibus. That's all.

---

