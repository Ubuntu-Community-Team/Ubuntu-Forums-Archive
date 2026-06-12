---
title: "Release upgrade to LTS"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by mindbox2 on 2014-03-31
I know that the option "**Long term support releases only**" for
the "**Software Sources/Updates/Show new distribution releases**" GUI
a[COLOR=#333333][FONT=Ubuntu]llows an upgrade between Long Term Support releases ([/FONT][/COLOR][community docs]("https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab")[COLOR=#333333][FONT=Ubuntu]).

Moreover, in "[/FONT][/COLOR]**/etc/update-manager/release-upgrades**" can be read:

[I]Note that this option should not be used if the currently-running release
is not itself an LTS release, since in that case the upgrader won't be able
to determine if a newer release is available.
[/I]
From what I understand that if I select this option in 13.10 I won't be
advertised about the incoming 14.04 LTS release. I cannot understand
the reasoning behind this behavior or the limitation implied by the 
*"won't be able"* above.

Besides, shouldn't that be advised also in the GUI?

Thanks for your responses.

---

### Post by ibjsb4 on 2014-04-01
You could upgrade now.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo do-release-upgrade -d
```

---

