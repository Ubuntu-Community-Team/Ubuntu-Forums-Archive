---
title: "Issue in the .bashrc file where &quot;shopt&quot; command is invalid"
date: 2024-03-09
forum: Installation &amp; Upgrades
---

### Post by priyesh777 on 2024-03-09
The problem occured when I was trying to set the "export JAVA_HOME" variable in the bash file manually. 

Step 1: I added the "export JAVA_HOME" variable in the bashrc file
Step 2: After adding the variable i tried to do "source ~/.bashrc" 
Step 3: The problem occured stating the following error:
   ``` 
/home/priiyesh/.bashrc:16: command not found: shopt
/home/priiyesh/.bashrc:24: command not found: shopt
/home/priiyesh/.bashrc:28: command not found: shopt
/home/priiyesh/.bashrc:111: command not found: shopt
/usr/share/bash-completion/bash_completion:45: command not found: shopt
/usr/share/bash-completion/bash_completion:1596: parse error near `|

```

Step 4: I re-installed the bash 2 times but still the issue wasn't solved

#Note: I have also attached the bash file below:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case$-in
*i*) ;;
*)return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt-shistappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt-scheckwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
shopt-sglobstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval"$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case"$TERM"in
xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
if [ -x /usr/bin/tput ] && tputsetaf1 >&/dev/null; then
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
unsetcolor_promptforce_color_prompt

# If this is an xterm set the title to user@host:dir
case"$TERM"in
xterm*|rxvt*)
PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
test-r~/.dircolors && eval"$(dircolors-b ~/.dircolors)" || eval"$(dircolors-b)"
aliasls='ls --color=auto'
#alias dir='dir --color=auto'
#alias vdir='vdir --color=auto'

aliasgrep='grep --color=auto'
aliasfgrep='fgrep --color=auto'
aliasegrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
aliasll='ls -alF'
aliasla='ls -A'
aliasl='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
aliasalert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
.~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt-oqposix; then
if [ -f /usr/share/bash-completion/bash_completion ]; then
./usr/share/bash-completion/bash_completion
elif [ -f /etc/bash_completion ]; then
./etc/bash_completion
fi
fi

exportNVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \."$NVM_DIR/nvm.sh"# This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \."$NVM_DIR/bash_completion"# This loads nvm bash_completion

## Added Custom Java_Home variable
exportJAVA_HOME=/usr/share/java

```



#Note: Any help would be highly appreciated.

---

### Post by ajgreeny on 2024-03-09
> **priyesh777 said:**
> The problem occured when I was trying to set the "export JAVA_HOME" variable in the bash file manually. 

Step 1: I added the "export JAVA_HOME" variable in the bashrc file
Step 2: After adding the variable i tried to do "source ~/.bashrc" 
Step 3: The problem occured stating the following error:
   ``` 
/home/priiyesh/.bashrc:16: command not found: shopt
/home/priiyesh/.bashrc:24: command not found: shopt
/home/priiyesh/.bashrc:28: command not found: shopt
/home/priiyesh/.bashrc:111: command not found: shopt
/usr/share/bash-completion/bash_completion:45: command not found: shopt
/usr/share/bash-completion/bash_completion:1596: parse error near `|

```

Step 4: I re-installed the bash 2 times but still the issue wasn't solved

#Note: I have also attached the bash file below:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case$-in
*i*) ;;
*)return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt-shistappend  # should be [COLOR="#FF0000"]shopt -s histappend[/COLOR]

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt-scheckwinsize # should be [COLOR="#FF0000"]shopt -s checkwinsize[/COLOR]

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
shopt-sglobstar # should be [COLOR="#FF0000"]shopt -s globstar[/COLOR]

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval"$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case"$TERM"in
xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
if [ -x /usr/bin/tput ] && tputsetaf1 >&/dev/null; then
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
unsetcolor_promptforce_color_prompt

# If this is an xterm set the title to user@host:dir
case"$TERM"in
xterm*|rxvt*)
PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
test-r~/.dircolors && eval"$(dircolors-b ~/.dircolors)" || eval"$(dircolors-b)"
aliasls='ls --color=auto'
#alias dir='dir --color=auto'
#alias vdir='vdir --color=auto'

aliasgrep='grep --color=auto'
aliasfgrep='fgrep --color=auto'
aliasegrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
aliasll='ls -alF'
aliasla='ls -A'
aliasl='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
aliasalert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
.~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt-oqposix; then # should be [COLOR="#FF0000"]shopt -oq posix; then[/COLOR]
if [ -f /usr/share/bash-completion/bash_completion ]; then
./usr/share/bash-completion/bash_completion
elif [ -f /etc/bash_completion ]; then
./etc/bash_completion
fi
fi

exportNVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \."$NVM_DIR/nvm.sh"# This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \."$NVM_DIR/bash_completion"# This loads nvm bash_completion

## Added Custom Java_Home variable
exportJAVA_HOME=/usr/share/java

```



#Note: Any help would be highly appreciated.

In the quoted post I have shown how the faulty lines should look and marked them in red.
Your file has lines with missing spaces which you need to edit as I show.

Open the hidden ***.bashrc*** file in your home using a text editor and make those changes and all should be well.

---

### Post by priyesh777 on 2024-03-10
Thankyou so much for your response. I did applied the spaces but it didn't work. And the main issue is the "shopt" command is not found when I tried "shopt -v" so I was guessing all of this cause is due to the shopt command not being installed properly. And I bash automatically downloads the "shopt" command due which I won't be able to install it separately

---

### Post by MAFoElffen on 2024-03-10
No. Note what ajgeeny told you...

If you put it into a code editor and search on shopt, you will find that it occurs 4 times. At lines 16, 24, 28 and 111.

In each of those lines, the spaces between all of those, somehow all the spaces between all them got removed between the shopt command, its flag and options, so it trys to interpret it all as a one word command, which is not there.

Look at line 16:
```

# yours
shopt-shistappend
# should be:
shopt -s histappend

```
At line 24
```

# yours
shopt-scheckwinsize
# should be
shopt -s checkwinsize

```
At line 28
```

# Yours
shopt-sglobstar
# Should be
shopt -s globstar

```
At line 111
```

# Yours
if ! shopt-oqposix; then
# should be 
if ! shopt -oq posix; then

```
You see and understand that right?

"shopt" is the BASH internal command.

Quoted from: [Ubuntu BASH Man Page]("https://manpages.ubuntu.com/manpages/jammy/en/man1/bash.1.html") 
> 
```

Syntax
      shopt [-pqsu] [-o] [*optname* ...]

Options
     -s   Enable (set) each optname

     -u   Disable (unset) each optname.

     -p   Display a list of all settable options, with an indication of 
          whether or not each is set. The output is displayed in a form 
          that can be reused as input. (-p is the default action)

     -q   Suppresses normal output; the return status indicates whether the optname
          is set or unset. If multiple optname arguments are given with '-q',
          the return status is zero if all optnames are enabled; non-zero otherwise. 

     -o   Restricts the values of optname to be those defined for the '-o' option to 
          the set builtin.
```


---

### Post by MAFoElffen on 2024-03-10
Oh right further... Since "shopt" is an internal BASH Command, if BASH is the shell interpreter, it's there.

Since not an external command it will not be found with 'which', but...
```

$ type shopt
shopt is a shell builtin

```

---

