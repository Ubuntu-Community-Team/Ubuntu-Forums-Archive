---
title: "After re-install user permissions are screwy"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by EmilyRose on 2013-06-04
So, I've upgraded/re-installed the same way many, many, many times over the years. And for the first time I've run into problems. My basic reutine is to format my / partition and leave /home in tact. This has always worked fine in the past... This time around, most things seem to work, but my account while it *is* an admin account does not appear to have full admin privileges - I don't seem to have permission to write on usb disks, for example. Initially I thought this was a problem with the usb flash drives but am now fairly sure it in fact has to do with user permissions. I'm currently running Ubuntu-GNOME 13.04 - previously I had Ubuntu-GNOME 13.04 beta installed - fwiw I've re-installed 3 possibly 4 times always with the same result (regardless of using the same password or different, and always with the same user name). I've finally gotten Ubuntu 13.04 downloaded and may attempt to install it next time around if need be.

---

### Post by papibe on 2013-06-04
Hi EmilyRose.

Could you post the output of these commands?
```
id

sudo cat /etc/sudoers

ls -ldn ~
```
Regards.

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]EmilyRose;
Permission issues ?? Very likely.
Is the variable XAUTHORITY set ?
```
echo $XAUTHORITY
```
Does your user_name have access to "/home" ?
```

ls -la ~/.ICEauthority
ls -la ~/.Xauthority

```

That will start a process of looking/fixing.
[/COLOR][INDENT][COLOR=#000000]
hope this helps

[/COLOR][/INDENT]

---

### Post by EmilyRose on 2013-06-04
id: 
uid=1000(emily) gid=1000(emily) groups=1000(emily),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),125(sambashare)

sudo cat:

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d


ls ldn ~:
drwxrwxr-x 78 1000 1000 12288 Jun  4 15:47 /home/emily

echo XAUTHORITY:
/run/gdm/auth-for-emily-xUUYFt/database


Finally ls -la ~/ICEauthority produces:
-rw-rw-r-- 1 emily emily 64094 Jun  3 11:25 /home/emily/.ICEauthority

and ls -la ~/Xauthority:
-rw-rw-r-- 1 emily emily 59 Jun  1 07:54 /home/emily/.Xauthority

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]EmilyRose; Hey;

IDK ...all except the variable XAUTHORITY appears good to me...from your output you got it's location, not if the variable is set - bet now that it is -- anyway double check; the "$" says we want the value of the variable:
```
 echo $XAUTHORITY
```[INDENT]
wrong, but I am willing to learn better

[/INDENT]
 [/COLOR]

---

### Post by papibe on 2013-06-04
> **EmilyRose said:**
> echo XAUTHORITY:
/run/gdm/auth-for-emily-xUUYFt/database
If that was really 'echo $XAUTHORITY', then it seems you are using config files from 10.10, where the ~/.Xauthority was no loger used.

Could you post the result of these commands?
```
grep -i xau ~/.bashrc ~/.profile /etc/bash.bashrc

diff ~/.bashrc /etc/skel/.bashrc 

diff ~/.profile /etc/skel/.profile 
```
Regards.

---

### Post by EmilyRose on 2013-06-05
grep -i xau ~/.bashrc ~/.profile /etc/bash.bashrc:

grep: /home/emily/.profile: No such file or directory

diff ~/.bashrc /etc/skel/.bashrc: 

1c1,114
< PATH=/usr/local/bin:/usr/bin:/bin:/usr/games:/home/emily/.local/bin:/home/emily/.local/bin
---
> # ~/.bashrc: executed by bash(1) for non-login shells.
> # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
> # for examples
> 
> # If not running interactively, don't do anything
> case $- in
>     *i*) ;;
>       *) return;;
> esac
> 
> # don't put duplicate lines or lines starting with space in the history.
> # See bash(1) for more options
> HISTCONTROL=ignoreboth
> 
> # append to the history file, don't overwrite it
> shopt -s histappend
> 
> # for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
> HISTSIZE=1000
> HISTFILESIZE=2000
> 
> # check the window size after each command and, if necessary,
> # update the values of LINES and COLUMNS.
> shopt -s checkwinsize
> 
> # If set, the pattern "**" used in a pathname expansion context will
> # match all files and zero or more directories and subdirectories.
> #shopt -s globstar
> 
> # make less more friendly for non-text input files, see lesspipe(1)
> [ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"
> 
> # set variable identifying the chroot you work in (used in the prompt below)
> if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
>     debian_chroot=$(cat /etc/debian_chroot)
> fi
> 
> # set a fancy prompt (non-color, unless we know we "want" color)
> case "$TERM" in
>     xterm-color) color_prompt=yes;;
> esac
> 
> # uncomment for a colored prompt, if the terminal has the capability; turned
> # off by default to not distract the user: the focus in a terminal window
> # should be on the output of commands, not on the prompt
> #force_color_prompt=yes
> 
> if [ -n "$force_color_prompt" ]; then
>     if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
> 	# We have color support; assume it's compliant with Ecma-48
> 	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
> 	# a case would tend to support setf rather than setaf.)
> 	color_prompt=yes
>     else
> 	color_prompt=
>     fi
> fi
> 
> if [ "$color_prompt" = yes ]; then
>     PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
> else
>     PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
> fi
> unset color_prompt force_color_prompt
> 
> # If this is an xterm set the title to user@host:dir
> case "$TERM" in
> xterm*|rxvt*)
>     PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
>     ;;
> *)
>     ;;
> esac
> 
> # enable color support of ls and also add handy aliases
> if [ -x /usr/bin/dircolors ]; then
>     test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
>     alias ls='ls --color=auto'
>     #alias dir='dir --color=auto'
>     #alias vdir='vdir --color=auto'
> 
>     alias grep='grep --color=auto'
>     alias fgrep='fgrep --color=auto'
>     alias egrep='egrep --color=auto'
> fi
> 
> # some more ls aliases
> alias ll='ls -alF'
> alias la='ls -A'
> alias l='ls -CF'
> 
> # Add an "alert" alias for long running commands.  Use like so:
> #   sleep 10; alert
> alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
> 
> # Alias definitions.
> # You may want to put all your additions into a separate file like
> # ~/.bash_aliases, instead of adding them here directly.
> # See /usr/share/doc/bash-doc/examples in the bash-doc package.
> 
> if [ -f ~/.bash_aliases ]; then
>     . ~/.bash_aliases
> fi
> 
> # enable programmable completion features (you don't need to enable
> # this, if it's already enabled in /etc/bash.bashrc and /etc/profile
> # sources /etc/bash.bashrc).
> if ! shopt -oq posix; then
>   if [ -f /usr/share/bash-completion/bash_completion ]; then
>     . /usr/share/bash-completion/bash_completion
>   elif [ -f /etc/bash_completion ]; then
>     . /etc/bash_completion
>   fi
> fi

and diff ~/.profile /etc/skel/.profile

returns no such file or directory...

and echo $XAUTHORITY produces:
/run/gdm/auth-for-emily-xUUYFt/database

---

### Post by papibe on 2013-06-05
Thanks.

Do you have the guess account enable? If so, try logout from your account and login into the guess account and check what this produces:
```
echo $XAUTHORITY
```
If it is either empty or points to a home file like this:
```
/home/guess/.Xauthority
```
Then it means it is a problem with your account instead of a system configuration.

In that case, I'd suggest to change your config files for the ones on the skel directory.

First backup your current ones:
```
mv  ~/.bashrc  ~/.bashrc.old

mv  ~/.profile  ~/.profile.old

mv  ~/.bash_logout  ~/.bash_logout.old
```
Then copy the files from skel to your home directory
```
cp -v /etc/skel/.[bp]* ~/
```
Logout and in again.

Let us know how it went.
Regards.

---

### Post by EmilyRose on 2013-06-08
That fixed it! I actually appear to have not had a profile OR bash_logout file/folder, so perhaps that was part of the problem. THANK YOU!!! :) :) :)

---

### Post by papibe on 2013-06-08
:D Great! **Bashing-om** pointed us in the right direction.

When you have the chance please mark the thee thread as solved,  ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Regards.

---

