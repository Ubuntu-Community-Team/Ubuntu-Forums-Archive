---
title: "Adobe Photoshop CS2 Need help with HOWTO"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2008-01-18
I am trying to install Adobe Photoshop CS2 with wine and i am going off this HOWTO i found online.
[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps]("http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps")

But this step gives me problems.

> In your Windows box, type &#8220;regedit&#8221; in the command-line and export the whole &#8220;HKEY_LOCAL_MACHINE/Software/Adobe/&#8221; to &#8220;adobe.reg&#8221;.

The next step is to copy that file to your Ubuntu box and convert it to the encoding of YOUR system. For example, if your Ubuntu box has as default charset ascii and your Windows box has ucs-2 then &#8220;$ recode ucs-2..ascii adobe.reg&#8221; would do the trick. After you converted your adobe.reg file, type &#8220;$ sudo wine regedit adobe.reg&#8221; to import it to wine.

I don't understand the charset ascii and I don't think I did the whole regedit thing corrently?  would someone mind explaing it to me?

I am under Ubuntu 7.10 Gutsy, Adobe Photoshop CS2, and under XP Professional.

Thank you,
Sugi

---

### Post by staticvoid on 2008-01-18
not sure... but alternativly...

when you install photoshop it will ask for a key

you can use free key retrieving software. google it. then you just put in your key.

I have done photoshop CS2 on my lappy, happy :D

sv

---

### Post by Sugi on 2008-01-18
im trying to import a reg file from windows for my adobe photoshop cs2 file.  but i can't get this command to work
 "$ $ recode ucs-2..ascii adobe.reg
bash: $: command not found"   
How do I fix this?

---

### Post by Sugi on 2008-01-18
> :~/.wine$ recode ucs-2.ascii adobe.reg
recode: Request `ucs-2.ascii' is erroneous
:~/.wine$ sudo wine regedit adobe.reg
wine: /home/LongPENIS/.wine is not owned by you

What should I do now?

---

### Post by oldsoundguy on 2008-01-18
Just an FYI .. I left my Adobe stuff on my Windows computers and installed GIMP in Ubuntu.  If that program was not FREE, Adobe would be in court over it!  TREMENDOUS on line documentation for it, also!  The only thing missing from that  is way cool in CS2 is Adobe Bridge.

---

### Post by Sugi on 2008-01-19
Don't get me wrong, GIMP is the sh*t, but I have been a PhotoShop, Illustrator, Indign, etc. for almost 4 years now and GIMP just doesn't cut it anymore for my more advance needs.  I need some help getting CS2 to work.

Please, Someone help me.

Thanks,
Sugi

---

### Post by Mongoose.wa on 2008-01-20
I'm with Sugi. GIMP's lack of blending effects and good text-manipulation tools made it difficult to adjust to for my web design projects.

I've gotten CS2 to install through Wine, but I'm left with it not being able to activate. Plus, it takes forever for it to load.

EDIT: Scratch that. CS2 works perfectly for me as of 0.9.54

---

