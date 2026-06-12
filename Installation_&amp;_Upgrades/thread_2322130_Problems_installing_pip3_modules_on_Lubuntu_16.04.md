---
title: "Problems installing pip3 modules on Lubuntu 16.04"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by groovychap on 2016-04-26
I'm using Lubuntu 16.04 LTS and attempting to learn Python.

The version of Python I'm using is 3.5.1, which comes installed by default.

I'm working through a book called 'Automate the Boring Stuff', which requires the installation of several modules.

I've installed most of them without difficulty, but there are four which are causing me problems.

When I enter: 

> sudo pip3 install imapclient

I get [this]("http://pastebin.com/vt6y2efw") error.

When I enter:

> sudo pip3 install pyzmail

I get [this]("http://pastebin.com/bgKebc1A") error.

When I enter:

> sudo pip3 install pillow

I get [this]("http://pastebin.com/7CNLQ5gU") error.

And when I enter:

> sudo pip3 install pyautogui

I get [this]("http://pastebin.com/1bKA8Kg8") error.

Could you help me make sense of them?

---

### Post by groovychap on 2016-04-27
All of my error messages contained the text:

> [COLOR=#333333][FONT=Consolas]If executing pip with sudo, you may want sudo's -H flag.[/FONT][/COLOR]

I've tried using the -H flag whilst attempting to install all four modules, but with no success.

These are errors I received whilst using the -H flag: [imapclient]("http://pastebin.com/ehHZiWbu"), [pyzmail]("http://pastebin.com/H02u9NWA"), [pillow](http://pastebin.com/huZvL7U7), [pyautogui]("http://pastebin.com/qc79FWzX")

I should mention that I also was unable to install these modules on Lubuntu 15.10, which suggests that this isn't a 16.04 problem.

---

