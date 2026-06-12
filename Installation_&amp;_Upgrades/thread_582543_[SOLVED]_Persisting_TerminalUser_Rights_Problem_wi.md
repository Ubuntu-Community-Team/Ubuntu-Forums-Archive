---
title: "[SOLVED] Persisting Terminal/User Rights Problem with FakeRAID Guide and Gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by xcafeus on 2007-10-19
Hi guys,

Today I tried a fresh install of Gutsy on my Desktop PC which has 2x 80GB disks as RAID0 and WindowsXP. I followed the FakeRAID HowTo and after rebooting I noticed there was no sound. That happened to me in the past and I discovered that using the FakeRAID guide at first boot the User (me) has no sound rights, restricted devices are not shown and the Terminal has a strange prompt. See screenshot (the characters in the terminal are produced by pressing the arrow keys):

[[IMG]http://img88.imageshack.us/img88/9474/screenshotvz7.th.png[/IMG]](http://img88.imageshack.us/my.php?image=screenshotvz7.png)

What has gone wrong again and why us, raid0 users, still have to go through all this? Please note that I installed Gutsy on my HP dv6520ea Laptop and I have no sound and it is almost impossible to run Compiz without messing everything up. 

I am a very patient person - stubborn you might say - which means that I do not give up so easily BUT this Gutsy situation (i realise im not alone either) is driving me mad. I got two non-functional computers (almost) with UBUNTU!I cant sleep! Please advise.

This is my /root/.bashrc
-------------------------------------
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
#export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi
-------------------------------------------------------
Thank you in advance.
x

---

### Post by xcafeus on 2007-10-20
the funny thing is that I get sound at the login screen. Then its gone when I log in...

---

### Post by xcafeus on 2007-10-20
ok incase this happens to you here is what you do:

system->preferences->main menu ...find main menu, then go to administration and find login windows, right click-properties, copy the command. open the terminal and run the command so that the login preferences pop up... enable from security->allow login as root. then again from main menu find users and groups. right click copy the commande and paste it in terminal. Users preferences will pop up, go to root and set a password.

LOGOUT (not switch user) and login with u: root, p: the_password_you_set. Now you are logged in as "root" got to users from administration and DELETE your screwed up username. Go to Places-Computer-File System-Home and delete faulty user directory (becarefull backup any needed files). Again go to Users and re-add the user you want. Logout and relogin with the User. Thats it.

It is recommended for safety that you now dis-allow the option to login as root from the Login preferences.

Sorry that there are no Terminal commands - Im a noob.

---

### Post by skattman83 on 2007-10-22
> **xcafeus said:**
> 
LOGOUT (not switch user) and login with u: root, p: the_password_you_set. Now you are logged in as "root" got to users from administration and DELETE your screwed up username. Go to Places-Computer-File System-Home and delete faulty user directory (becarefull backup any needed files). Again go to Users and re-add the user you want. Logout and relogin with the User. Thats it.


Every time that I set up the user account, it looks like it gets created, but then when I close and reopen the users and groups window, the user account is not there.  Any ideas on whats going on here?

---

### Post by xcafeus on 2007-10-23
I know the oposite (the "faulty" account cannot be DELETED when you are looged in as root) is happening because I used "Switch User" and not Logout. So the faulty user is still logged in the background and thus root cannot delete it. You say althought you manage to delete the account then you cannot create it again?? thats weird ...did you try to restart ..log in as root and then try to create it again?

Im sorry man Im not very knowledgable with Ubuntu.. the steps I describe above I found them out myself so when something goes wrong I dont really know what to do ....I keep trying..

---

