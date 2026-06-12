---
title: "Script for creating restore point in Ubuntu"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by zynex on 2012-12-20
Hi.

This is a little script I been working on for easy creating a kind of basic "restore point" for linux. It doesn't actually back up any files per say, it just creates a list of all packages installed in the system, backing up all repositories and the keys for it.

In the script I take use of  "dpkg --clear-selections" and "apt-get dselect-upgrade" for restoring the system from the list the script makes. Make sure you know how this works before you use this script. 

Also, the script will fetch all repositories in /etc/apt/sources.list and /etc/apt/sources.list.d, but will only restore it into a single sources.list file.

The script is good for restoring a crashed system, transfer a mirror installation to another computer or just to use before installing new packages you want to test. If you don't want the packages installed, just use restore and the new packages will be uninstalled again.

You can also edit the script and modify the "function userscripts()" to add your own specifik scripts you use in your system. The ones included are some that I use myself (BankID installation and fix for Asus suspend).

Script:

```

#!/bin/bash
# lires v1.0
# Created by Michael Rydén 2012
# The script is free to use, copy and edit.
#
# This script makes a list of which packages are installed in the system, and also makes
# a backup of your current repositorys and their keys. These can be used to restore the
# system at a later point, or make a mirror installation on another computer.
#
#  Args:    -r - Restore from previous saved state
#            -b - Backup current system state
#            -s - Run user script
#            -h - Show help
#


rpfile=$HOME/.restorepoint

function script_usage()
{
    echo "Usage: `basename $0` -r -b [-s] [-h] <[FILE]>"
    echo "    -r    Restore previous saved state"
    echo "    -b    Backup current system state"
    echo "    -s    Run user script part"
    echo "    -h    Show this message"
    echo ""
    echo "FILE is an optional restorepoint file."
    echo "If no file is specified, the default filenames will be used."
    return
}

function backup()
{
    echo "Creating restorepoint for your system.."
    sudo dpkg --get-selections > $rpfile.list
    cat /etc/apt/sources.list /etc/apt/sources.list.d/*.list > $rpfile.repo
    sudo apt-key exportall > $rpfile.keys
}

function restore()
{
    if [ ! -f "$rpfile.keys" ]; then echo "$rpfile.keys dosn't exist, make a backup first!"; exit 0; fi
    if [ ! -f "$rpfile.repo" ]; then echo "$rpfile.repo dosn't exist, make a backup first!"; exit 0; fi
    if [ ! -f "$rpfile.list" ]; then echo "$rpfile.list dosn't exist, make a backup first!"; exit 0; fi

    echo 'Restoring system repositorys...'
    sudo apt-key add $rpfile.keys > /dev/null
    sudo cp $rpfile.repo /etc/apt/sources.list
    sudo apt-get -qq update

    #Restore previous installed packages and remove unwanted packages
    echo 'Restoring previous installed packages and remove unwanted packages..'
    sudo dpkg --clear-selections
    sudo dpkg --set-selections < $rpfile.list
    sudo apt-get -qq dselect-upgrade

    #Update system
    echo 'Updating system to current versions..'
    sudo apt-get -qq dist-upgrade
    
    #Do some cleanup
    echo 'Cleaning upp..'
    sudo apt-get -qq clean
    sudo apt-get -qq autoclean
}

function userscripts()
{
    echo 'Installing BankID..'
    mkdir BankID
    cd BankID
    wget --no-check-certificate -q -O BankID.tar.gz https://install.bankid.com/Download?defaultFileId=Linux
    tar -xf BankID.tar.gz
    cd BISP*
    sudo ./install*.sh i
    sudo nspluginwrapper -i /usr/local/lib/personal/libplugins.so
    cd ..
    rm -r BankID
    
    #Suspend fix
    echo '
#!/bin/sh
VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
echo -n > $DEV_LIST 2>/dev/null
for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
    echo -n "$dev" > $DDIR/unbind
    echo "$driver $dev" >> $DEV_LIST
    done
done
}

bindDev() {
if [ -s $DEV_LIST ]; then
    while read driver dev; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
        echo -n "$dev" > $DDIR/bind
        if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
        else
            break
        fi
        MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
    done  
    done < $DEV_LIST
fi
rm $DEV_LIST 2>/dev/null
}

case "$1" in
hibernate|suspend) unbindDev;;
resume|thaw)       bindDev;;
esac
' | sudo tee -a /etc/pm/sleep.d/20_custom-ehci_hcd > /dev/null
    sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

}

if [ $# == 0 ]; then script_usage; exit 1; fi

while getopts ":rbsh" opt; do
    case $opt in
        r) r=1;;
        b) b=1;;
        s) s=1;;
        h) script_usage; exit 0;;
        \?) echo "Invalid option: -$OPTARG" >&2; exit 1;;
  esac
done

if [ "$r" == "1" -a "$b" == "1" ]; then script_usage; exit 1; fi

shift $(( OPTIND-1 ))
if [ $1 ]; then rpfile=$1; fi

if [ "$b" == "1" ]; then backup; fi
if [ "$r" == "1" ]; then restore; fi
if [ "$s" == "1" ]; then userscripts; fi
echo "Done."

```To use it, save the script and make it executable. Run **lires -b** to make a backup, and **lires -r** to restore previous backup. You can also specify your own name for the backup files with **lires -b <file>**. If you want to run the user scripts after you restored the system, use **lires -rs**.

Have fun! :)

--Mike

---

