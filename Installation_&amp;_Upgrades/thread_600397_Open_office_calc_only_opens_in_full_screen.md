---
title: "Open office calc only opens in full screen"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by waylow on 2007-11-02
Hey there

I upgraded Ubuntu to 7.10 - most things are working correctly but now open office calc will only open in full screen and it has no window around it (doesn't have the little minimize and x buttons in the top right)

all the other open office apps run correctly - just calc that is playing up

anybody know how I can make it behave?

thanks

wayne

---

### Post by Deathmoon on 2007-11-02
I have the same issue, except it's the word processor that is doing this.  I covers the panels on top and bottom of the screen.

if I open up calc (it's not doing this) and the open the document, the screen is fine; it's only when i open word processor

---

### Post by Deathmoon on 2007-11-02
Also, the dialog box that appears (save, discard, cancel) takes up the full screen.  I see no title bars; and again this is only in word processor.

---

### Post by waylow on 2007-11-02
yep this is the same with me (only calc)

has anybody got any suggestions on how to fix it?

---

### Post by waylow on 2007-11-05
If you turn off desktop effects it works

the problem is something to do with compiz
I don't know how to get it to work with desktop effects running but at least it works

i will keep playing with it

---

### Post by Rudi Völler on 2007-11-05
I have the same problem with oocalc. If you Alt + tab to another open application, right click on the oocalc icon in the application panel and go to Advanced, you can disable the fullscreen mode. Then maximize oocalc and it looks ok. But the problem with dialog boxes taking up the full screen is still there. This way you don't have to turn off desktop effects. 

Is there a bugreport somewhere for this?...

---

### Post by henriquemaia on 2007-12-12
> **Rudi Völler said:**
> I have the same problem with oocalc. If you Alt + tab to another open application, right click on the oocalc icon in the application panel and go to Advanced, you can disable the fullscreen mode. Then maximize oocalc and it looks ok. But the problem with dialog boxes taking up the full screen is still there. This way you don't have to turn off desktop effects. 

Is there a bugreport somewhere for this?...

I just came accross this issue. I tried reinstalling openoffice without success, but then I installed openoffice.org-gnome (and gtk dependency) package, restarted oocalc and the issue was gone.

---

### Post by FokkerCharlie on 2007-12-28
Hi all

I had a similar problem, so tried installing -gnome, which solved it, and also made the dialogs work better.  However, I now have a fonts problem- the characters on menus, row/col headers etc are displayed as small rectangles.  Fonts within documents look fine.

Any ideas?

Thanks
Charlie

---

### Post by FokkerCharlie on 2007-12-28
OK- solved my little issue by de-selecting 'Use System Font for User Interface' in Tools>Options>View.

Cheers!
Charlie

---

### Post by samden on 2008-05-01
I had exactly the same issue with calc after upgrading to Hardy. I found this solution on another forum, and it worked for me:

Install the "Advanced desktop effects settings" package (Compiz desktop effects control panel), you can just go to add/remove applications for this.

In this control panel:
- Enable "Workarounds"
- Within "Workarounds", disable "Legacy full screen support"

I hope this helps someone.

---

### Post by edwinjayr on 2008-07-01
Guys,

Try this one. I found it in another forums. It worked for me.

Go into your Home directory, press Ctrl+h to show all hidden files, find the file called ".openoffice.org2" and rename it by adding an "A" to the end of its name" so that it becomes ".openoffice.org2A".

Open Openoffice Writer or any other Openoffice program and the problem should be resolved. Openoffice will generate a fresh ".openoffice.org2" file.

When everything works to your satisfaction, you can delete the file you renamed.

---

