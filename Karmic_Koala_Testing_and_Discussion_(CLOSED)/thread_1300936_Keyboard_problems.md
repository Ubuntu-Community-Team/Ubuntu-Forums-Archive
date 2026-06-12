---
title: "Keyboard problems"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by breem42 on 2009-10-25
Hi all

I recently went through the only slightly painful (but slow) process of upgrading from Hardy to Karmic.  Halfway through (probably in Jaunty) I noticed that some of the keys on my generic 104 keyboard were not working right.  I just kept going with the upgrades, hoping it would sort itself out, but it did not.

Specifically
- the key left of the "1" is completely wrong - should produce alternate single quote, but I get "#", and tilde, but I get "|",
- the "at" key (shift 2) now produces a double quote (")
- shift 3 produces "/" instead of "#".
- shift 6 produces "?"

There are more, but it is too painful to try typing them all in.  You will notice I have not used a apostrophe in this post, because that key has a peculiar effect.  Typing "apostrophe a" produces "à".

Could this all be because I told ubuntu that I was in Canada, and it assumed I was using a French Canadian keyboard?

(BTW I just discovered that trying to type a "/" gets me a "é" and trying to type a "?" gets a "É".  Charming.)

EDIT------
Going to System-Preferences-Keyboard-Layout does not seem to offer much help.

---------------------------------

Since I cannot reply to this message, I will just add the info I have found.  When I type

```
setxkbmap -model pc104 -layout us
```

my keyboard starts working correctly.  I don't know yet how to make this change permanent.

---------------------------------

Workaround to make change "permanent";

1) Go to System/Preferences/Startup Programs
2) Make sure you are on the "Startup Programs" tab and click "Add"
3) I typed "US Keyboard Mapping" for Name, and "setxkbmap -model pc104 -layout us" for Command.  Of course, your keyboard may be different.
4) Click "Add"

Next time you log in, the command will be executed, and your keymap will be changed.

This is just a workaround.  I think the real solution involves Hal and editing some sort of SGML (.fdi) file, but I don't know what that change is.

Hope this can help someone.

---

