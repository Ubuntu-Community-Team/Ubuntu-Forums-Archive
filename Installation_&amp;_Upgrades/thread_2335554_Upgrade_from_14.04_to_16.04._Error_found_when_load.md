---
title: "Upgrade from 14.04 to 16.04. Error found when loading /home/user/.profile"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by joe196 on 2016-08-30
Upgraded from 14.04 to 16.04 and receive the following error:

```
Error found when loading /home/username/.profile:

/home/username/.profile: line 24 /opt/qt55/bin/qt55-env.sh: No such file or directory.

As a result the session will not be configured correctly.
You should fix the problem as soon as feasible.

```

My /home/username/.profile has:

```

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.


# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022


# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

There's no line 24 in .profile so I have no idea where to solve it.
How can this be fixed?

---

### Post by joe196 on 2016-08-30
Rookie error here. I was looking at the wrong .profile
The right profile had that line, I just needed to comment it.

---

