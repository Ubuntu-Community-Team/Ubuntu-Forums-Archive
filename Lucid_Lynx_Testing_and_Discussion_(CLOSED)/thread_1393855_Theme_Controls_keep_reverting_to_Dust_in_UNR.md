---
title: "Theme Controls keep reverting to Dust in UNR"
date: 2010-01-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gkumar on 2010-01-29
Hello, all,

I recently installed Ubuntu Netbook Remix 10.04 on my Acer Aspire One. The thing is, I can't seem to change the controls in my theme. Here's what I do:

I open up System>Preferences>Appearance, and with the *Custom* theme selected, I choose the customize button. Then, when the Customize Theme window pops up, the controls are set to Dust. The thing is, when I change it, it changes the controls as expected, but only in the open Appearance windows, and what's worse, when I reopen Appearance, it goes right back to Dust. I really can't stand the Dust controls, since they make many bars in various programs this odd gray gradient, and it doesn't mix well at all with the dark theme of the rest of UNR.

The odd thing is, this behavior only occurs when I choose the Netbook session on login. GNOME doesn't revert that setting. I quite like the netbook remix way of organizing the desktop, so I'd prefer to stick with that and have my controls set up correctly, rather than exclusively use GNOME.

Any help in the right direction would be wonderful.

Thanks!

---

### Post by snkiz on 2010-01-29
sounds like gnome settings daemon isn't running, however that's just a guess with the limited info you gave. But every time I've run into that scenario the settings daemon has been the cause.

---

### Post by gkumar on 2010-01-29
I just tried running gnome-settings-daemon, but that didn't change anything. Another oddity that I think is related is this: Whenever I choose a system theme straight from the appearance window, it applies it, but then almost instantaneously changes to custom, with the new theme's window border and such applied to *Custom*, as if it just changed a few settings in the *customize theme *window automagically. If it helps, I think it might have something to do with whatever it is that manages these settings. I tried killing netbook-launcher and maximus, and that didn't seem to do the trick. If there's any more relevant info that would be helpful, let me know.

---

### Post by snkiz on 2010-01-30
> **gkumar said:**
> I just tried running gnome-settings-daemon, but that didn't change anything. Another oddity that I think is related is this: Whenever I choose a system theme straight from the appearance window, it applies it, but then almost instantaneously changes to custom, with the new theme's window border and such applied to *Custom*, as if it just changed a few settings in the *customize theme *window automagically. If it helps, I think it might have something to do with whatever it is that manages these settings. I tried killing netbook-launcher and maximus, and that didn't seem to do the trick. If there's any more relevant info that would be helpful, let me know.

Nope that was all I had, really. well you ARE on an alpha release so the next step I would think is to file a bug. Since your not sure what package is causing the issue I say look at the unr bug tracker here: [https://bugs.launchpad.net/netbook-remix]("https://bugs.launchpad.net/netbook-remix")

---

