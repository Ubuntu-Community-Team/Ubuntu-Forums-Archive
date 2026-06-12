---
title: "Something happened to Terminal and bashrc after upgrade"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by Semn on 2017-07-24
Hi, just upgraded some 2 weeks ago on Ubuntu 16.04 a recent upgrade, and when the computer rebooted, the new terminal which appeared is different from the previous,

the font is different and the computer name in the command line is underlined, so it looks like:

_Sem_:~>

Now, this is not really a problem it self, but it was accompanied by that previously working scripts, such as MATLAB and miniconda, don't any longer  call to bashrc on loading a new terminal. I have these two lines as the end of bashrc, and they have virtually no effect at all, and no matlab command is found, unless I go into that directory manually, and type in ./matlab.

# added by Miniconda2 4.3.21 installer
export PATH="/home/sem/miniconda2/bin:$PATH"

export PATH="/home/sem/MATLAB/R2017a/bin/:$PATH"

This was not a problem before the upgrade and the weird change of terminal appearance. 

Does anyone have an idea what this can be caused by, and how to fix it?

---

### Post by steeldriver on 2017-07-24
You changed your default shell (to `fish` maybe?) or modified your terminal to use a different shell as its 'Custom command'?

Check with

```

echo $SHELL

getent passwd $USER

```

and/or opening the terminal `Profile preferences` --> `Command`

---

### Post by Semn on 2017-07-25
Hi, thanks for this, seems it  has switched over to tcsh. I used a terminal with green username highlighted in bold...how can I go back to it?

Sem:~> echo $SHELL
/usr/bin/tcsh
Sem:~>

---

### Post by steeldriver on 2017-07-25
First, check whether tcsh is set as your login shell:

```

getent passwd $USER

```

(look at the last field) - if it is, then simply run

```

chsh -s /bin/bash

```

as your regular user.

OTOH if $SHELL is being set elsewhere (e.g. your login shell is still bash, but your ~/.bashrc switches to tcsh) then you will need to find and revert those changes.

---

