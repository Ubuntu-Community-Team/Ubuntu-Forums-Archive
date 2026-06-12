---
title: "SCIM and GUTSY"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by longfeng on 2007-10-13
i`ve tried now to install the the GUTSY and its works very well.

i have only one small "problem" with SCIM and the input table.

When i start (SCIM simplified Chinese) i get the table at the left bottom.

What can i do that the table comes direct under the input line?

Thanks

---

### Post by mhenriday on 2007-10-19
Well, **Longfeng**, you are either luckier or more skilful than I (or both) ! I've just upgraded from **Feisty** to **Gutsy** and am very pleased with the new version. But in connexion with the upgrade, **SCIM** was updated from version **1.4.4** to version **1.4.7**, and I now find myself unable to start the application. Despite the fact that running ```
scim -d
```in a terminal places the **SCIM** icon on my panel, I cannot open the **SCIM** menu by clicking on it, as was my wont in **Feisty**. Right-clicking on the icon, however, opens the settings menu for **SCIM**, precisely as in the earlier **Ubuntu** version. Any suggestions as to how I can get **SCIM** to work, so that I can enter text in **CJK** languages directly from my keyboard ?...

Henri

---

### Post by aaginskiy on 2007-10-19
I am having the same issue with the lookup tables sticking to one corner, instead of displaying under the current typing place.  I don't think it did so in previous version.  I tried to play around with the settings, but with no luck.  Anyone found a solution to this?

Thanks!

---

### Post by Hustle Kong on 2007-10-19
I'm not able to use SCIM now at all to switch between English and Japanese since the upgrade...

---

### Post by yookoala on 2007-10-19
I'm no expert. I think the update may change stuffs in xinit.d or similar folders.
You may try to reinstall SCIM and related package by reinstall the Language Support.
[list=1]
[*]go to Setting -> Language Support
[*]click your own language type and apply it again
[/list]

---

### Post by jon.reeve on 2007-10-19
I'm having the same problem. I figured out how to get the left-click menu to come back by playing around with it a lot, that is, opening the SCIM configuration again and enabling / disabling Chinese support, enabling a hotkey, clicking on 'reload SCIM configuration' in the right-click menu, clicking on the 'enable complex character support' in Language Support. 

But I still can't get the input menu list of characters to stick under the input... can move it by dragging it but can't get it to follow text yet. Grrr....

---

### Post by longfeng on 2007-10-19
maybe, but i working with ubuntu 4 weeks now, several times i have installed, the last was a beta 7.10.

So i have no skill level of UBUNTU.

Well i have checked it again. Today, why ever, the function is ok, close to the cursor position, and i did nothing.

i`ve installed it 

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

installed language:
English, Chinese and German

activate the input method complex 

and why ever, its running now...........................


regards

Klaus

---

### Post by moon2js on 2007-10-20
I couldn't change input language after upgrading to Gutsy. (No keyboard icon in the tray, keyboard shortcut didn't bring up language bar.) I just went to SCIM and unticked, applied, reticked, and reapplied my second language. Then I restarted the system (because I was too lazy to figure out how to specifically restart SCIM). And it worked fine.

---

### Post by aaginskiy on 2007-10-20
I am still having the same problem with the lookup table not floating to the right position.  It seems that the lookup table always goes to the bottom left of whatever text field you are typing in, rather to below the line you are on.

Perhaps I will try to compile scim from the current source code, rather than obtain it from repositories.

In the mean time, if anyone has any suggestions on how to fix it, I would greatly appreciate it.

---

### Post by mhenriday on 2007-10-22
**Jon.reeve** and** aaginskiy**, try adjusting the general settings under «**Front End**». I have checked «**Use the same input method for all programmes**», but _unchecked_ «**Show unconverted Latin letters in your working window**» ; these settings work very well for me !...

In return, I have a problem with adding languages (orthographies), for which I could use a little help : when I (left-)click on the **SCIM** icon, I can choose among the following :
[LIST]Chinese simplified
Chinese traditional
Japanese
Korean
Latin letters
Other[LIST]
[*]Western
[*]Sourcecode
[/LIST]
[/LIST]
I should also like to add Greek and Czech, for which I have enabled language support under **System** &#8594; **Administration**, but have been unable to find a way to do so. In **SCIM 1.4.4**, which was the default version under** Feisty**, one could right-click the **SCIM** icon to access the settings window, and then check the desired languages from a long list in «**General Settings**» under the** IMEngine**. Now under **Gutsy**, however, I see only Japanese, Korean, Chinese (simplified), Chinese (traditional), and «Other», and no method to add other languages. Any ideas ?...

Henri

---

### Post by jon.reeve on 2007-10-22
Henri, I might be totally wrong about this, but I was under the impression that SCIM was only really meant to be an input method app allowing you to write complex scripts like Chinese and Japanese that can't otherwise be inputted using a normal keyboard. Greek and Czech, as far as I know, have alphabets that can be mapped using a keyboard layout and shouldn't require an input method app as a go-between. To switch between English and French, for example, I have a widget on my panel that's a keyboard layout switcher (should come standard) and I've set up one keyboard layout as US English and another as Canadian French, and I just click the icon in the panel which switches between the two. This of course requires that you know where all the keys are in your language's keyboard layout, otherwise it might be a little confusing at first. 

Thanks for the help with SCIM, I'll give that a try when I get home today.

---

### Post by mhenriday on 2007-10-23
**Jon**, here, among other things, is what the **SCIM** [Features]("http://www.scim-im.org/about/features") page has to say about the matter :
> The goal of SCIM:

    * Act as an unified frontend for current available input method libraries. Currently bindings to uim and m17n library are available.
    * Act as a language engine of IIIMF input method framework (TBD).
    * Provide as many native IMEngines as possible.
    * Support as many input method protocol/interface as possible.
    * Support as many operating systems as possible.

Myself, while I am aware of the fact that there are other methods, I have previously found it convenient to use **SCIM** to switch between the various orthographies I needed to use. There are, of course, many ways to skin a cat, but best is that to which one is accustomed....

Have you succeeded in getting** SCIM** to place the lookup table nearer the line into which you are typing ? And what do you see when you open «**General Settings**» under the **IMEngine** ?...

Henri

---

### Post by jon.reeve on 2007-10-24
Wow, great, it seems that unchecking that box solved the problem! :) Under en_US, the box is called "embed preedit string into client window".  

Under "IMEngine," I just have two groups, Chinese and "other," and under "other" there's just "English/European" and RawCode. While a previous version of SCIM may have had the option to switch between different european languages, it's always seemed to me that SCIM handles, as you quoted previously, input *methods*, not just different keyboard maps. An input method being, for example, a complicated piece of software for looking up Chinese pinyin letters or zhuyin in a table to get a list of corresponding characters, as opposed to a keyboard map which just allows you to type different European letters. From what I can tell, in the case of European languages, the system itself is the input method.

---

### Post by jenhsun on 2007-10-24
Check it out this bug
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

After I enable the complex input to fireup SCIM, keyboard freeze for input.
This problem only in Gutsy 32 and 64 bits only.

FYI

---

### Post by mhenriday on 2007-10-27
**Jenhsun**, are you still experiencing this problem ? I haven't encountered it myself....

Henri

---

### Post by satellite360 on 2007-10-28
** Never mind - finally got it working by unchecking and reapplying the settings in SCIM a number of times! **
[COLOR="Silver"]
I'm confused.  Seems I have been through all the recommendations in this and other threads and still when I left-click the SCIM icon nothing happens and the usual keyboard shortcut to change languages also has no effect.

Does anyone have any idea how to get this working?[/COLOR]

** Never mind - finally got it working by unchecking and reapplying the settings in SCIM a number of times! **

---

### Post by jenhsun on 2007-10-28
Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)

And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

