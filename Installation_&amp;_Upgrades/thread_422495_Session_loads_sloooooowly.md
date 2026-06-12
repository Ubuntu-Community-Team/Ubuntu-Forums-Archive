---
title: "Session loads sloooooowly"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2007-04-25
I just upgraded from Fiesty to Edgy, and I ran into a couple of problems.

1) The session items load only after some minutes. This is the biggest issue, since compiz-tray-icon is in there, and I have to wait a lot before it starts. It seems like something has greater priority and gets stuck, but I couldn't find how to set priority in Feisty. This problem is even more serious because of

2) With Metacity I don't have any window borders. I could expect this behaviour from Compiz-Beryl, but Metacity?? This first happened when I tried to enable desktop effects. I ran into problems, so I installed compiz-tray-icon, which loads Compiz fine, but doesn't solve the problem with Metacity.

3) This is a minor issue. The splash screen remains on the screen until I click on it. Not a real problem, but it's a strange behaviour.

---

### Post by Nonno Bassotto on 2007-04-26
Ok, I now realize that 3) is a consequence of 1). As soon as all items have been loaded, the splash screen goes away.

I wonder if the delay in 1) is a consequence of 2)

---

### Post by Hador on 2007-04-26
I've run into the same problem upon updating to Feisty. I managed to fix it deleting the **%HOME/.gnomerc** entry regarding *gnome-compiz-manager*.
I hope it'll work for you as well.

---

### Post by Nonno Bassotto on 2007-04-26
Wonderful!!! It works.

The side effect, though, is that now I can't logout early. The logout dialog can be used only after some minutes I have logged in. If I try to logout before nothing happens; then after some minutes the dialog appears. From then , it works, so if I cancel the action, the next times it works fine. :confused:

---

### Post by indrg on 2007-04-29
Hi.

I am experiencing the same problem now after upgrading from edgy to Feisty and installing Beryl. All day  I have  been playing with Beryl.  In the afternoon, I customized my Feisty by downloading new gdm window login themes, new splash screens.  I also played around with sessions with Beryl.  

Suddenly, the splash screen remained on the screen and it took a while to get the logout dialog to show up.
I retraced my steps including removing the splash screens, the gdm window login themes and eventually Beryl, Beryl Manager and Beryl Settings, and Emerald Themes.

However I am still having this problem.  

Do you guys have suggestions how to fix this?  I suspected setting session to default to Beryl one time caused this long session loads.

I don't think I have %HOME/.gnomerc.  I have $HOME/.beryl-managerrc file but I don't think this is it.

Any idea is greatly appreciated.

Thanks.
-Indra

---

### Post by Nonno Bassotto on 2007-04-29
The file .gnome2/session contains everything your session loads at start. Try removing (or temporarily renaming, if you want to restore it later) this file. Then add the session items you want with the dialog System->Preferences->Session

---

### Post by indrg on 2007-04-29
Hi Nonno,

Thank you very much.  It works.  No more splash screen stuck on desktop in long session and logout dialog immediately appears right away.  I reinstall Beryl, add mew splash screen.  

Thanks.
-Indra

---

### Post by randell6564 on 2007-04-29
> I just upgraded from Fiesty to Edgy...
How did you do THAT?  Edgy is an older version. If you can do that, then PLEASE create a tutorial so that others can do the same when thier system breaks!
Lol!:confused:

---

### Post by Nonno Bassotto on 2007-04-29
Ok, ok, but you get the point...

---

