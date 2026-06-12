---
title: "Post-Install script"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by rcrcomputing on 2008-08-16
This is a post-install script I run after a new installation of debian or ubuntu. You should not just download this and run it. You need to look at it and edit it to your liking. Here's what it does:

apt-get update
replaces /etc/networking/interfaces with your version (nice to have examples).
installs a decent /root/.bashrc  gvimrc and vimrc
uses sed to keep numlox on in /etc/console-tools/config
Optionally installs stuff like arj zoo and many others
Optionally removes ppp pppoe etc..
Installs cron-apt and sets up a schedule for it.

My personal copy also sets up apt and sources, though I removed that option here.

All config files that it affects are first backed up with a .tweak extention, ex. interfaces will be backed up to interfaces.tweak. Future runs will NOT replace the .tweak file so you can always get back your configuration before running the script.  Have been running this script for several years, so it should be safe enough, though I urge caution as you may get unexpected results.

Again, this is NOT a "everyone download and run" script. It is meant to be edited to your liking and to make the initial setup on a desktop or server much faster.

If nothing else, it may be a good tool for learning some simple things you can do with a bash script. 

Lastly, be aware, it will NOT ask for confirmation to replace the /etc/network/interfaces file. Though it will backup the original.

I suggest you edit it, test in a virtualbox till you get it just the way you want it.

Hope you find it useful as I do..  Any suggestions are certainly welcome!  Enjoy..

```

#!/bin/bash
#Of course, put this file in the /bin directory and chmod 755 /bin/post_tweak

green="\033[1;32m"
red="\033[1;31m"
yellow=" \033[1;33m"
blue="\033[1;34m"
purple=" \033[1;35m"
cyan="\033[1;36m"
white="\033[1;37m"
normal="\033[0;39m"
blink="\033[5m"


clear


echo -e ${green}Showing users currently connected... $normal
w
echo -e $green Executing as $USER $normal


if [ "$USER" = "root" ]
then

        echo -e $green Good, you are $USER, we shall contine $normal

else

        echo -e $red You must be root user to run this script Aborting... $normal
   exit 1
fi




apt-get update

apt-get install vim lynx bzip2 unzip ntpdate unzoo arj zip lzop nomarch arc zoo rar lha dnsutils module-assistant postfix rcconf perl dpkg apt apt-utils debconf traceroute dnsutils net-tools sysutils dnswalk ntop netmask cron-apt

apt-get remove pppoe pppoeconf ppp pppconfig uw-imapd


#******************
#BashRC Stuff
#******************

if [ -f ~/.bashrc.tweak ]

      then 
	echo -e $blue  Backup of bashrc.tweak exists! We will not overwrite it. skipping... $normal
      else
	echo -e $green  Backing up bashrc file! $normal
	cp ~/.bashrc ~/.bashrc.tweak
fi
        

	echo -en $yellow "Replace Current users .bashrc .vimrc and .gvimrc files? $cyan [no] (y/N)"
        read answer
        if expr "$answer" : ' *[yY].*' > /dev/null; then


cat > ~/.bashrc <<"End-of-file"
#--------------Post-Install Tweaked Bashrc-----------------------

export PS1="\[\e[36;1m\]\H \[\e[32;1m\]\w> \[\e[0m\]"
umask 022

# You may uncomment the following lines if you want `ls' to be colorized:
export LS_OPTIONS='--color=auto'
eval `dircolors`
alias ls='ls $LS_OPTIONS -F'
alias ll='ls $LS_OPTIONS -l'
alias l='ls $LS_OPTIONS -lA'
#
# Some more alias to avoid making mistakes:
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
alias aai="aptitude install"
alias aas="aptitude search"
alias aar="aptitude remove"
alias aau="aptitude update"
alias aauu="aptitude upgrade"
alias aadu="aptitude dist-upgrade"
alias sv="/etc/init.d/"
alias agr="apt-get remove"
alias acs='apt-cache search'
alias agi="apt-get install"
alias agu="apt-get update"

#edit the last file you opened
alias lvim="vim -c \"normal '0\""


. /etc/bash_completion
#--------------Post-Install Tweaked BashRC-----------------------

End-of-file





#******************
# Gvimrc section
#******************

if [ -f ~/.gvimrc.tweak ]

      then 
	echo -e $blue Backup of original file gvimrc exist, skipping ... $normal
      else
	echo -e $green  Backing up Gvimrc file! $normal
	cp ~/.gvimrc ~/.gvimrc.tweak
fi

cat >~/.gvimrc<<"End-of-file"
set background=dark
set guifont=monospace\ 16

colorscheme blue " my color scheme

if has("gui_kde")
        set guifont=helvetica/16/-1/5/50/0/0/0/0/0
endif
End-of-file




#******************
# Vimrc section
#******************

if [ -f ~/.vimrc.tweak ]

      then 
	echo -e $blue  Backup of original file vimrc exist, skipping ... $normal
      else
	echo -e $green  Backing up Vimrc file! $normal
	cp ~/.vimrc ~/.vimrc.tweak
fi


cat > ~/.vimrc <<"End-of-file"
"#--------------Post-Install Tweaked Vimrc-----------------------
set background=dark
set ignorecase

" When started as "evim", evim.vim will already have done these settings.
if v:progname =~? "evim"
  finish
endif

" Use Vim settings, rather then Vi settings (much better!).
" This must be first, because it changes other options as a side effect.
set nocompatible

" allow backspacing over everything in insert mode
set backspace=indent,eol,start

if has("vms")
  set nobackup		" do not keep a backup file, use versions instead
else
  set backup		" keep a backup file
endif
set history=50		" keep 50 lines of command line history
set ruler		" show the cursor position all the time
set showcmd		" display incomplete commands
set incsearch		" do incremental searching

" For Win32 GUI: remove 't' flag from 'guioptions': no tearoff menu entries
" let &guioptions = substitute(&guioptions, "t", "", "g")

" Don't use Ex mode, use Q for formatting
map Q gq

" This is an alternative that also works in block mode, but the deleted
" text is lost and it only works for putting the current register.
"vnoremap p "_dp

" Switch syntax highlighting on, when the terminal has colors
" Also switch on highlighting the last used search pattern.
if &t_Co > 2 || has("gui_running")
  syntax on
  set hlsearch
endif

" Only do this part when compiled with support for autocommands.
if has("autocmd")

  " Enable file type detection.
  " Use the default filetype settings, so that mail gets 'tw' set to 72,
  " 'cindent' is on in C files, etc.
  " Also load indent files, to automatically do language-dependent indenting.
  filetype plugin indent on

  " Put these in an autocmd group, so that we can delete them easily.
  augroup vimrcEx
  au!

  " For all text files set 'textwidth' to 78 characters.
  autocmd FileType text setlocal textwidth=78

  " When editing a file, always jump to the last known cursor position.
  " Don't do it when the position is invalid or when inside an event handler
  " (happens when dropping a file on gvim).
  autocmd BufReadPost *
    \ if line("'\"") > 0 && line("'\"") <= line("$") |
    \   exe "normal g`\"" |
    \ endif

  augroup END

else

  set autoindent		" always set autoindenting on

endif " has("autocmd")

set nocindent
set nosmartindent
set noautoindent
"#set indenexpr=
filetype indent off
filetype plugin indent off
hi Search ctermbg=Grey
hi Search ctermbg=Blue

"#--------------Post-Install Tweaked Vimrc-----------------------
End-of-file



        else

           echo -e $blue  User chooses to skip bashrc gvimrc and vimrc Configuration ... $
normal
        fi




#*********************************
#**** Static Network settings ****
#*********************************


if [ -f /etc/network/interfaces.tweak ]

      then 
	echo -e $blue  Backup of original file /etc/network/interfaces exist, skipping ... $normal
      else
	echo -e $green  Backing up /etc/network/interfaces file! $normal
	cp /etc/network/interfaces /etc/network/interfaces.tweak
fi



cat >/etc/network/interfaces<<"End-of-file"
	
#--------------Post-Install Tweaked Network Settings-----------------------

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# List possibility of static settings below
#iface eth0 inet static
#        address 192.168.0.50
#        netmask 255.255.255.0
#        network 192.168.0.0
#        broadcast 192.168.0.255
#        gateway 192.168.0.1

#iface eth0 inet static
#        address 192.168.1.50
#        netmask 255.255.255.0
#        network 192.168.1.0
#        broadcast 192.168.1.255
#        gateway 192.168.1.1

#--------------Post-Install Tweaked Network Settings-----------------------
End-of-file


# Try to set Linux's fetish with jacking with the numlock key.  :(

if [ -f /etc/console-tools/config.tweek ]
	then 
		echo -e $blue  Backup of original file config.tweak exists, skipping... $normal
	else
		cp /etc/console-tools/config /etc/console-tools/config.tweek
		echo -e $green Editing /etc/console-tools/config to set numlock ON at boot... $normal
		sed -i.tweak 's/#LEDS=+num/LEDS=+num/' /etc/console-tools/config
fi

if [ -f /etc/cron.d/cron-apt.tweek ]
	then 
		echo -e $blue  Backup of original file config.tweak exists, skipping... $normal
	else
		cp /etc/cron.d/cron-apt /etc/cron-apt.tweak
		echo -e $green Backing up /etc/cron.d/cron-apt to /etc/cron-apt.tweak... $normal
		echo -e $green Editing /etc/cron.d/cron-apt to run daily with no email output... $normal
		echo "@daily root /usr/sbin/cron-apt && /usr/sbin/cron-apt >/dev/null 2>&1" > /etc/cron.d/cron-apt
fi

echo
echo -e $yellow Please set /etc/apt/apt.conf if you need a proxy setup. $normal
echo -e $yellow Please set the /etc/hostname if needed. Host name is $HOSTNAME $normal
echo
echo -e $purple Post-Install Tweaks installed Have a nice day! $normal

```

---

