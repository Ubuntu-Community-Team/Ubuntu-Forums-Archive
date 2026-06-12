---
title: "Odd autocorrect issue after upgrading to 18.04"
date: 2019-03-31
forum: Installation &amp; Upgrades
---

### Post by rachel.o on 2019-03-31
Hello, I'm in the USAand Íve started seeing issues in Opera web browser after upgrading to Ubuntu 18.04. Previously I had Ubuntu 16.04. Ím not quite sure how to fix thi&#351; but so far Íve tried checking language setting&#351; checking keyboard setting&#351; and resetting Opera settings. 

The spelling errors you see in the previous paragraph (and in this one) are from this aut&#333;correct issu&#281; not from my typin&#289; Basically, Ím losing punctuation - it's converted to special characters sometimes- and occasionally spaces disappear. Also, if typing using all caps, there are no spaces:LIKESO,THEYJUSTDISAPPEAR when holding down shift. 

Resetting Opera settings resolved the issue for about 8 minutes, and then it's back to normal, same with changing the keyboard settings from system default. Sometimes when typing, I'm able to type normally - like now - and then it will go back eventually. 

I'm not observing this behavior in chrome, but it's also not happening right at this moment in Opera (although you can see it happening earlier). 

USAkeyboard language - oh it's back agai&#326; Ím not surprised - not sure what other information I can supply that would be usefu&#320; Ye&#351; that was a period. I am comfortable with using the command lin&#281; if there is any further information or commands to be used.

Edit: It's happening in Chrome also. Not sure if it's system-wid&#281; I have&#324;t typed everywhere yet.

---

### Post by Rubi1200 on 2019-03-31
Hi and welcome to the forums!

Can you please test whether this also happens in a text editor and/or writing applications such as LibreOffice so we can exclude those and determine if the issue is browser related or something else.

I would also temporarily disable auto-correct in both browsers to see what the results bring.

Thanks.

---

### Post by rachel.o on 2019-03-31
Thanks for the reply, Rubi! It looks like the issue happens in LibreOffice also.

---

### Post by Rubi1200 on 2019-03-31
Open a terminal and try this command to reset the keyboard layout:

```
setxkbmap -layout us
```

This will reset the keyboard to use U.S. as the default.

You may have to log out and in again for the changes to take effect.

---

### Post by rachel.o on 2019-03-31
Thanks, I gave that a try but it didn't work. 

Turns out it was some area of the settings called "input method" - I turned off/deleted a ton of things, unfortunately not sure which was it. It was shift + space that was triggering the alternative layout, I suppose it was something added or changed in the update that I missed. Not sure how to mark this as solved.

---

### Post by Rubi1200 on 2019-04-01
I'm glad you managed to get this sorted out in the end.

It's been awhile since I was active on the forum but you used to be able to go to Thread Tools at the top of the post and in the drop-down you can mark solved.

Failing that, edit your thread title and insert solved there.

Best of luck.

---

