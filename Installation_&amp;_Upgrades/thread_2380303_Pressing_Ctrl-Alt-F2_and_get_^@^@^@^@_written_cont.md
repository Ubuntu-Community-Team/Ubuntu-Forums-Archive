---
title: "Pressing Ctrl-Alt-F2 and get ^@^@^@^@ written continuously"
date: 2017-12-15
forum: Installation &amp; Upgrades
---

### Post by rodrigohernan-ramos on 2017-12-15
install ubuntu 17.04 and as the title says it is written continuously ^ @ ^ @ ^ @ ^ @ and so without stopping.
I open the console and 
execute:sudo showkey -k
and the output is as follows
Press any key ...(the program ends 10 seconds after the last key press)
key code 213 pressedkey 
code 213 released
so in an infinite loop

Search everywhere, it is not a letter that is kept precedente because that combination is not possible in a keyboard.

I did
xmodmap -pke and find this:
keycode 213 = XF86Suspend NoSymbol XF86Suspendplease,


 I do not know what to doFrom already thank you very much!!!

---

### Post by QIII on 2017-12-15
Hello!

Please use English in this area of the forums.  Don't worry if English is not your native language.  Just do your best and we will do our best to help you.  :)

You may also give one of our LoCo (Local Community) sub-forums a try if you need help in your native language.  We want to make sure you get the assistance you need.

Cheers!

---

