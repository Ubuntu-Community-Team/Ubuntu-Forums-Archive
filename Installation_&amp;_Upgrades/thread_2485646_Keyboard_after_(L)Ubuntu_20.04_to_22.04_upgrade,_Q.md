---
title: "Keyboard after (L)Ubuntu 20.04 to 22.04 upgrade, Qt, fcitx, umlaut letters"
date: 2023-04-05
forum: Installation &amp; Upgrades
---

### Post by xinuzi on 2023-04-05
[SIZE=3]**Goal:**[/SIZE] 

Type umlaut letters by just pressing Shift+topdoubledotaccent+letter (e,i,u,o) (on azerty keyboard).
As in the German '[COLOR=#ff0000]**ü**[/COLOR]bermensch' (hyperhuman) or in the Dutch + Flemish 'be[COLOR=#ff0000]**ï**[/COLOR]nvloeden' (influence).
Good to know is, although the same language (with tiny differences), the Dutch use the anglo-saxon qwerty keyboard layout and the Flemings the French azerty keyboard layout. 

[SIZE=3]**Situation:**[/SIZE]

Taskbar (bottom panel) keyboard icon activates an alert (see image attachment).
Confirming it opens a configuration file in text editor.
fcitx not launched.

Screenshot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292026&stc=1[/IMG]


[SIZE=3]**Actions taken:**[/SIZE]

- Remove fcitx and all its components in synaptic packet manager. Icon disappears from bottom panel (after reboot).
- Restart.
- Go to Menu -> Preferences -> LXQT Settings -> Keyboard and Mouse -> Keyboard Layout.
Notice the remark: "*If you are using an **Input method**, such as IBus, uim, fcitx, or gcin, the settings here **might not work** because they are overriden by the input methods*" 
If you are a Belgian/Fleming and you want the umlaut keys, the keyboard layout '**Belgian (no dead keys)**' won't work.
What does seem to work is: '**Belgian (Wang 724 AZERTY)**'...
Click the 'Add' button and move that setting to the top.
The Germans will probably just add German.

Screenshot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292027&stc=1[/IMG]


Not sure if it is necessary to remove fcitx.
Less is More and it could always get reinstalled if needed.

Other useful advise welcome.

---

### Post by ActionParsnip on 2023-04-05
What is the output of:
```

dpkg -l | grep -i fcitx; lsb_release -a; uname -a

```
Thanks

---

### Post by xinuzi on 2023-04-06
> **ActionParsnip said:**
> What is the output of:
```

dpkg -l | grep -i fcitx; lsb_release -a; uname -a

```
Thanks

It's okay.
The thing is solved.

---

