---
title: "bash default directory"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vttay03 on 2009-10-04
I've noticed in Karmic that when I open a shell, I am in the root directory - how do I change this so that it defaults to my home directory instead?  I thought it was probably somewhere in the '.bashrc' file but nothing is really jumping out at me....any ideas?

---

### Post by eric3_14159 on 2009-10-04
Well, I'm not sure what is causing it, but if you put a "cd ~" line at the bottom of your .bashrc file, that will at least fix the immediate problem.

---

### Post by bogdan.veringioiu on 2009-10-05
Hi.

What is hour $HOME variable value?
Type:
echo $HOME

Bogdan

---

### Post by homeofpoe on 2009-10-05
> **bogdan.veringioiu said:**
> Hi.

What is hour $HOME variable value?
Type:
echo $HOME

Bogdan

I have the same issue as the OP, and the $HOME variable is the standard "/home/myusername".

Also, when saving files via Firefox, it also defaults to the root directory.

---

### Post by vttay03 on 2009-10-05
echo $HOME produced the correct result so that wasn't the problem....as suggested above I placed:

```

cd ~

```

at the end of my .bashrc problem and that at least fixed the problem for the time being...still would be curious to know what is doing this though.

---

### Post by VMC on 2009-10-05
Type "env" from a terminal. That will give a listing of all your variables including home.

You also might check your users&groups to see that your setup correctly.

---

### Post by slakkie on 2009-10-05
I don't know why you have this behaviour, since I cannot reproduce it. I removed my .bashrc and I login directly to $HOME.

Could you guys post your .bashrc?

---

### Post by homeofpoe on 2009-10-05
My **.bashrc** file:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

The output of **env** (replaced my username with UNAME):
```
ORBIT_SOCKETDIR=/tmp/orbit-UNAME
SSH_AGENT_PID=1533
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=3013779da8dc77e5c67d2bb44ac56244-1254621832.169480-1972210564
WINDOWID=92274693
GTK_MODULES=canberra-gtk-module
USER=UNAME
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/ssh-bZsuVh1494/agent.1494
GNOME_KEYRING_SOCKET=/tmp/keyring-faMeHk/socket
SESSION_MANAGER=local/chameleon:@/tmp/.ICE-unix/1494,unix/chameleon:/tmp/.ICE-unix/1494
USERNAME=UNAME
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/UNAME
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GNOME_KEYRING_PID=1479
GDM_LANG=en_US.UTF-8
GDMSESSION=gnome
SPEECHD_PORT=7560
SHLVL=1
HOME=/home/UNAME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=UNAME
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-4srp2c6eMK,guid=83aa30d881572bc03c0e68f24ac80288
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-UNAME-QhCIp3/database
OLDPWD=/
_=/usr/bin/env
```


This is on a fresh install of Ubuntu 9.10 Beta.

---

### Post by vttay03 on 2009-10-05
Output of env is below (my username replaced with user):

```

ORBIT_SOCKETDIR=/tmp/orbit-user
SSH_AGENT_PID=1991
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=62dca7117c8b0c52a6b9654c4ac6714d-1254789428.744576-753506865
WINDOWID=4194309
GTK_MODULES=canberra-gtk-module
USER=user
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/ssh-iYKrqt1952/agent.1952
GNOME_KEYRING_SOCKET=/tmp/keyring-doVl1Z/socket
SESSION_MANAGER=local/user-linuxdev:@/tmp/.ICE-unix/1952,unix/user-linuxdev:/tmp/.ICE-unix/1952
USERNAME=user
DESKTOP_SESSION=gnome
PATH=/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/user
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GNOME_KEYRING_PID=1937
GDM_LANG=en_US.UTF-8
GDMSESSION=gnome
SPEECHD_PORT=7560
SHLVL=1
HOME=/home/user
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=user
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Nt7aZicWg9,guid=bc7e615943c61f357feb19994aca9135
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-user-QpkvUu/database
OLDPWD=/home/user/conky_weather
_=/usr/bin/env

```

Like homeofpoe, I'm basically on a fresh install of Karmic Beta.

---

### Post by VMC on 2009-10-05
Both "env" outputs look normal. Almost identical to mine.

You can eliminate ".bashrc" is a source of your problem by temporally renaming it and fire up a terminal again.

---

### Post by mc4man on 2009-10-05
This sorta stands out
> OLDPWD=/

---

### Post by vttay03 on 2009-10-05
same thing when I renamed .bashrc and re-opened a shell - I came up in the root directory again.  I reckon adding the 'cd ~' statement in the .bashrc is a decent workaround, I would just like to know why it's not defaulting to my home directory.  Maybe just some type of behavior exhibited by Karmic Beta?  Definitely don't have this problem in 9.04....

---

### Post by VMC on 2009-10-05
> **mc4man said:**
> This sorta stands out

That's what I thought at first, but vttay03 output "OLDPWD=/home/user/conky_weather", contradicts that.

Edit: Just for grins I set that variable (OLDPWD=/) and mine still works correctly. as my ~/home directly.

---

