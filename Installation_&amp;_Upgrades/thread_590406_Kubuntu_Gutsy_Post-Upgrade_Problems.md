---
title: "Kubuntu Gutsy Post-Upgrade Problems"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by tjbk_tjb on 2007-10-24
Yesterday, I decided to upgrade my 64-bit Kubuntu Feisty Fawn to Gutsy Gibbon. So, I went and followed the instructions on the wiki. After some initial difficulty, the update program came up and started upgrading. 3 hours later, it said it had to restart some things. I noticed that it said gdm on the list. Since I didn't have gdm, I exchanged that for kdm and pressed continue. My X server preceded to restart. But the upgrade program did not. So I went on the forum for help. I read recommendations of the use of 'dpkg --configure -a' and 'apt-get upgrade.' I tried that a few times, along with the use of Aptitude to resolve problems. So, I think I'm all ready to go. Terminals say "7.10" and KDE has a shiny new theme.
Then I try to run Thunderbird. It doesn't start. I try it in the terminal. I get:
```
/usr/lib/thunderbird/thunderbird-bin: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
```
Later, I tried Firefox when I was having trouble with Flash (which was easily resolved by installing a package). Same message. Firefox was working, but only with kgtk-wrapper, which I installed manually. But that didn't help with GIMP, Abiword, or Thunderbird, all of which returned the same error. I tried reinstalling libgtk2.0-0 (package responsible for /usr/lib/libgdk-x11-2.0.so.0), but that doesn't help.

So, can anyone help me with this?

---

