---
title: "The keyboard has gone to hell."
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by Gorky on 2012-03-10
Hi 
I am new to Ubuntu.
My keyboard is not working.

I can't use the key board. It has gone to hell.
When I press the key 'p', the 'r' is coming to the screen.
When I pres the'n' key, 'l' comes to the screen.
Please help me to solve the problem. I tried in vain to fix the problem. 

I am new to Ubunutu. **It seems Ubuntu gives more problems for lay people.**
I can't use Kubuntu at all.
My Kubuntu version is 11.10
My computer has an AMD processor. It is a desktop computer.
**Please help me.**

PS
I am writing to you using one of my Windows based portable computer.

---

### Post by sudodus on 2012-03-10
Hi Gorky

It seems you have a keyboard for another language. What version and flavour of Ubuntu are you running? What language do you want to use, and what language has your physical keyboard?

---

### Post by Gorky on 2012-03-10
Thanks sudodus

My Kubuntu version is 11.10
I live in Sweden. I want Swedish. I don't mind keeping English.
Ubuntu is not very easy for beginners.
I have a Swedish keyboard. It worked fine with Mandriva and Fedora Core.
**Please help me.**

---

### Post by jfb112697 on 2012-03-10
in kubuntu system settings go to keyboard and see if there is a language thing i really dont use kubuntu or KDE at all so i wouldnt know

---

### Post by sudodus on 2012-03-10
It is not an issue between Swedish and English (or US) keyboard. It is something else.

1. Does it work with another keyboard?

2. Does it work if you boot the computer from the install CD or USB drive? (A 'live session' only testing, without installing.)

3. If it is a USB keyboard, can you test it in another USB port?

4. Can you check what keyboard should be installed?

5. Try the following command which should set a Swedish keyboard (if you can find the keys)
```
/usr/bin/setxkbmap se
``` but I also suggest that you look for the GUI tool, probably under the Settings menu. This tool can tweak several things, not only language but also the type of keyboard (number of keys etc).

---

### Post by Gins on 2012-03-11
Sudous
I've just came home from the gym and read your comments.

The following command worked and I could write those Swedish letters.
/usr/bin/setxkbmap se
[COLOR="SeaGreen"][B]
I am very glad. Keep a good watch on this thread. I might ask questions again.[/B][/COLOR]
[COLOR="Red"][B]
I hope this will be a permanent solution to the problem. I might ask questions again if this is not a permanent solution.[/B][/COLOR]
--------------------------------------------------------------------------------------------------------------------------------------------------
I rebooted the computer.
No this is not a permanent solution. I couldn't write Swedish letters and the same old problem remains.

Then I wrote the following you suggested:
/usr/bin/setxkbmap se
Everything worked fine. I could write the Swedish letters and it was normal.
[COLOR="Red"]So what is the real problem.[/COLOR]

---

### Post by sudodus on 2012-03-11
> **Gins said:**
> Sudous
I've just came home from the gym and read your comments.

The following command worked and I could write those Swedish letters.
/usr/bin/setxkbmap se
[COLOR="SeaGreen"][B]
I am very glad. Keep a good watch on this thread. I might ask questions again.[/B][/COLOR]
[COLOR="Red"][B]
I hope this will be a permanent solution to the problem. I might ask questions again if this is not a permanent solution.[/B][/COLOR]
I'm glad it works :-)

If you need it every time you boot, enter that line as the last one in the file .bashrc (bash running conditions) using an editor for example
```
nano ~/.bashrc
```
And then, as soon as you start a terminal window, you will get Swedish keyboard. If you add a terminal window to your startup programs, you will get it always. This is done in different ways depending on the flavour. You use Kubuntu and from the main menu you should select something like

System Settings -- Advanced -- Automatic Start

and get to a GUI where you enter your terminal window program.

---

### Post by Gins on 2012-03-11
Thanks for taking time to provide me with a swift reply.
Editing .bashrc file is a tall order for me.
I will try and let you know. 
**Please keep a good watch on this thread.**

---

### Post by Gins on 2012-03-11
I  have never ever edited .bashrc file.
I have never ever used the nano editor.
I know how to use the vi editor.

[B]The following is the output of the vi editor when I wrote 'vi ~/.bashrc' as a root user.
What shall I do?[/B]

```
~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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

"~/.bashrc" 99 lines, 3106 characters
 
```

---

### Post by Gins on 2012-03-11
[SIZE="3"]I would like to hear from you all again.[/SIZE]

---

### Post by sudodus on 2012-03-11
Add the line
```
/usr/bin/setxkbmap se
```
at the end of the file (that is after the last line) and save the file.

The next time you open a terminal or terminal window, it will set Swedish keyboard, because .bashrc is run before the terminal is handed over to you.

---

### Post by Gins on 2012-03-11
Thanks Sudodus for taking time again to help me.

I did what you suggested and the following is the .bashrc file.
The problem remains. To get the Swedish characters I must write the line you suggested.
/usr/bin/setxkbmap se
**What is the problem?**
```
a
root@nissanka-desktop:/home/nissanka# cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi
/usr/bin/setxkbmap se
 
```

---

### Post by sudodus on 2012-03-12
You managed to enter two lines in the beginning. Please remove them and save the file!
> **Gins said:**
> Thanks Sudodus for taking time again to help me.

I did what you suggested and the following is the .bashrc file.
The problem remains. To get the Swedish characters I must write the line you suggested.
/usr/bin/setxkbmap se
**What is the problem?**
```
[COLOR=Red]a
root@nissanka-desktop:/home/nissanka# cat ~/.bashrc[/COLOR]
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi
/usr/bin/setxkbmap se
 
```

---

### Post by sudodus on 2012-03-12
> **sudodus said:**
> ... And then, as soon as you start a terminal window, you will get Swedish keyboard. If you add a terminal window to your startup programs, you will get it always. This is done in different ways depending on the flavour. You use Kubuntu and from the main menu you should select something like

System Settings -- Advanced -- Automatic Start

and get to a GUI where you enter your terminal window program.

If you want this to happen always at login, you must also add a terminal window to your startup programs as I described before. In Kubuntu you are probably using ***konsole*** but you can use any flavour of terminal window program for example ***xterm***, they all run bash, so .bashrc is used to set the running conditions.

---

### Post by Gins on 2012-03-12
Thanks Sudodus for the reply.

System Administration    ---  Startup and shutdown

In 'Startup and shutdown', there are 3 items.
[B]1) Autostart
2) Service Manager
3) Session Management
[/B]
I added the console in 'Autostart'. In 'Autostart' , you have the opportunity to add programs; so I added the console.
So the console is in Autostart

I think the path is incorrect.
There is 'Work path'. I wrote '/usr/bin/setxkbmap se'. This can be changed. [B]I don't know the correct path.
[/B]
Type: desktop configuration file
Name: Konsole
Description: Terminal
Location:  home/nissanka/.config/autostart
Work path:/usr/bin/setxkbmap se

&#8230;......................................................................
[B]I looked at the icon 'Default Applications'.
It has the following:
Email client
Embedded text editor
File manager
Instant manager
Terminal Emulator
Web browser
Window manager[/B]
&#8230;........................................................................
I am not so good at these things. **What is the problem?**

I must write '/usr/bin/setxkbmap se' when I start the Kubuntu. My default operating system is Kubuntu

---

### Post by sudodus on 2012-03-13
> **Gins said:**
> ...
I think the path is incorrect.
There is 'Work path'. I wrote '/usr/bin/setxkbmap se'. This can be changed. [B]I don't know the correct path.
[/B]
Type: desktop configuration file
Name: Konsole
Description: Terminal
Location:  home/nissanka/.config/autostart
Work path:...
You should enter the full path to konsole, and it is listed when you run the command
```
which konsole
```
in a terminal window. It is something like
[FONT="Courier New"][SIZE="3"]/usr/bin/konsole[/SIZE][/FONT] but use your output from [FONT="Courier New"][SIZE="3"]which konsole[/SIZE][/FONT] as the correct path!

---

### Post by Gins on 2012-03-13
Thank Sudodus for taking time to reply me again.

The command 'which console' gave me the same output you wrote here.

```
nissanka@nissanka-desktop:~$ which konsole
/usr/bin/konsole
nissanka@nissanka-desktop:~$ 
 
```
So I've changed the work path to '/usr/bin/konsole'.
The problem remains.
What else could be the problem?
I hope you are not running out of ideas.
[COLOR="DarkGreen"]**Your thoughts are welcome.**[/COLOR]
-----------------------------------------------------------------
I did another change.
There is an icon called 'Country/Region & Language'.
I double clicked it and found only BrE and AmE. 

I asked the system to download Swedish. It worked fine. Then I made Swedish as the Preferred Language.
The problem still remains.

You could download French, German, Spanish, etc.

---

### Post by sudodus on 2012-03-14
1. At login, is a terminal command window started automatically?

- Otherwise, re-install konsole to the auto-started applications until that works!

2. When you start a terminal window, will it have Swedish keyboard?

- Otherwise, re-write ~/.bashrc so that its beginning is correct and that this command line is at the end of the file ```
/usr/bin/setxkbmap se
``` Maybe you should finish with an Enter (to get a new-line at the end of the file) before saving it.

Reboot and try again, and let us hope that it will work for you this time :-)

[I]Edit: You can test by running ```
source ~/.bashrc
```
You should get no error output.[/I]

---

### Post by whiskers751 on 2012-03-15
Don't add it to that file...

First, make a shell script to run on startup
```
sudo nano /etc/init.d/keyboardfixer
```
Then inside it type
```
#!/bin/bash
/usr/bin/setxkbmap se
exit
```

And then finally -
```
cd /etc/init.d/
sudo update-rc.d keyboardfixer defaults
```

Edit: Test with
```
sudo dash /etc/init.d/keyboardfixer
```

---

### Post by Gins on 2012-03-15
I thank both sudodus and Whiskers for taking time to reply me.
----------------------------------------------------------------------------
sudodus wrote the following:

1. At login, is a terminal command window started automatically?
No.
I rebooted several times to see whether this happens.
--------------------------------------------------------------------------
whiskers has suggested a new item.
**I will try it and let you know.**

---

### Post by sudodus on 2012-03-15
> **Gins said:**
> I thank both sudodus and Whiskers for taking time to reply me.
----------------------------------------------------------------------------
sudodus wrote the following:

1. At login, is a terminal command window started automatically?
No.
I rebooted several times to see whether this happens.
--------------------------------------------------------------------------
whiskers has suggested a new item.
**I will try it and let you know.**

Yes try the tip by* whiskers751*!

I don't know why my solution is not working for you, because I use it without problems in one of my computers. (In my other computers, it is not necessary.) The operating system is not the same version and flavour of Ubuntu as yours, so I cannot tell you exactly what to do in your particular menu system, but the general idea is the same, and the action behind the curtains should be the same.

---

### Post by sudodus on 2012-03-15
I tried it in a live boot from the kubuntu iso file (with default US-English keyboard)
- edited .bashrc and saved it
- entered konsole into the auto-start group

- logged out and in again
- and I had Swedish keyboard

Looking at the attached picture should help you doing it too

Good luck :-)

---

