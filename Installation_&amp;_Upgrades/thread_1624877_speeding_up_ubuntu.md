---
title: "speeding up ubuntu?"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by KegHead on 2010-11-18
Hi!

Does this really work?

 if [ "$PS1" ] ; then  
           mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
           echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
   fi

KegHead

---

### Post by dino99 on 2010-11-18
users on natty subforum (development) are very pleased at first glance, might be inserted into next 2.6.38 and is already used into server kernels for a while now.

---

### Post by KegHead on 2010-11-18
Hi!

Thanks for your reply!

I'll wait for the update.

Thanks!

KegHead

---

### Post by dino99 on 2010-11-18
nothing coming in the next days/weeks, only users tweakings

[http://newyork.ubuntuforums.org/showthread.php?t=1623940](http://newyork.ubuntuforums.org/showthread.php?t=1623940)

---

### Post by KegHead on 2010-11-18
Hi!

I'm a little gun shy on major tweaking.

Is there an easy to understand guide?

Thanks!

KegHead

---

### Post by dino99 on 2010-11-18
not yet, maybe you can try to PM these guys about their experience

[http://newyork.ubuntuforums.org/showpost.php?p=10127495&postcount=2](http://newyork.ubuntuforums.org/showpost.php?p=10127495&postcount=2)

---

### Post by KegHead on 2010-11-18
copy.

---

### Post by realzippy on 2010-11-18
from:

[http://lkml.org/lkml/2010/11/16/392](http://lkml.org/lkml/2010/11/16/392) :

[I]Here's my super-complex patch btw, to achieve exactly the same thing
> from userspace without involving any kernel or systemd patching and
> kernel-side logic. Simply edit your own ~/.bashrc and add this to the end:
> 
>   if [ "$PS1" ] ; then  
>           mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
>           echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
>   fi
> 
> Then, as the superuser do this:
> 
>   mount -t cgroup cgroup /sys/fs/cgroup/cpu -o cpu
>   mkdir -m 0777 /sys/fs/cgroup/cpu/user
> 
> Done. Same effect. However: not crazy.

[/I]

....no need for different kernel.Will check that out....

---

### Post by KegHead on 2010-11-18
hmm.

interesting.

KegHead

---

### Post by KegHead on 2010-11-18
Hi!

I edited and not sure there is any success.

I have an atom based (intel board)desktop w/2gb ram.

I also picked up the following in terminal:

bash: /home/jim/.bashrc: line 101: syntax error: unexpected end of file

Any ideas?

KegHead

---

### Post by realzippy on 2010-11-18
...there is no use (no speed up) in doing this,unless you run a **bunch** of tasks from tty.


See also e.g. .

[http://ubuntuforums.org/showpost.php?p=10127327&postcount=55](http://ubuntuforums.org/showpost.php?p=10127327&postcount=55)

---

### Post by KegHead on 2010-11-18
Hi!

I see,is there any way to get my system back to it's original state?

Thanks!

kegHead

---

### Post by corrytonapple on 2010-11-18
Maybe someone can post their file, if that is possible. Then you would have the original file (Somewhat).

---

### Post by realzippy on 2010-11-19
@ corrytonapple

...think OP only wants to get his *bashrc* back to original,not the whole system (read thread?  ;-) )

@ KegHead

Simply delete those added lines in ~/.bashrc

```
gedit ~/.bashrc
```

delete:

if [ "$PS1" ] ; then  
    mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
    echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
fi

---

### Post by dino99 on 2010-11-19
more info:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by KegHead on 2010-11-19
Hi!

I deleted and replaced the original lines with:

if [ "$PS1" ] ; then 
mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
fi

Does anyone know the original four lines?

Thanks!

KegHead

---

### Post by realzippy on 2010-11-19
...there are no original lines.You had to add it,not replace anything.... ?

---

### Post by KegHead on 2010-11-19
Yep,

Hard to believe, but I deleted those four lines and added your four.

I know...it was stupid.

KegHead

---

### Post by realzippy on 2010-11-19
> **KegHead said:**
> Yep,

Hard to believe, but I deleted those four lines and added your four.

I know...it was stupid.

KegHead

...maybe I posted a bit imprecisely.Anyway,if not sure you have the original status back,post your bashrc file.
Dino99 's link is interesting if you want further testing on this topic,seems as the solution you tried cannot work on ubuntu anyway...they have a ubuntu solution.

---

### Post by KegHead on 2010-11-19
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
if [ "$PS1" ] ; then
>       mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
>       echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
> fi

---

### Post by realzippy on 2010-11-19
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
[COLOR="SeaGreen"]if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi[/COLOR]
```

....this might have been your original file,before you added the "speedup" lines,(Corrected the last lines,seems as you did delete some stuff -marked it [COLOR="SeaGreen"]green[/COLOR]- accidentally...)

---

### Post by KegHead on 2010-11-19
Hi!

Your solution worked!

Thanks for your help!

KegHead

(I'll close entry)

---

### Post by libssd on 2010-11-21
> **KegHead said:**
> Hi!

I'm a little gun shy on major tweaking.

Is there an easy to understand guide?

Thanks!

KegHead
The best howto I have seen is here (scroll down to the section for Ubuntu): [http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html")

**NOTE**: These instructions were updated November 19 to correct a small logic error. 

As far as I can see, this alternative approach works fine with Ubuntu 10.04 LTS, and is much simpler to apply than compiling a custom kernel. In addition, it can be backed out quite easily. That said, because I didn't really understand how this works, I did a full backup prior to implementing these changes.:D

I did some A/B comparisons (but didn't time them), and the main improvements I have noticed have been with scrolling (long text files in gedit), page load speed (Google Chrome and Firefox), and video performance (video processing needs every bit of help it can get on a netbook); videos that previously stuttered at full screen now play smoothly.

---

