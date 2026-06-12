---
title: "I have a broken install and want to get system data from it"
date: 2023-02-11
forum: Installation &amp; Upgrades
---

### Post by kogorman-pacbell on 2023-02-11
I have a system that I really messed up.  The original OS installs won't start any more, so I'm trying to rebuild what they used to be.

The problem at the moment is package repositories.  I know I added some, but don't remember which ones.  The usual tool for getting at the lists is Software & Updates, which is a GUI app, which I cannot run in that environment.

I have created a bootable partition of the same release (20.04.5), so I can chroot and run CLI tools -- just not GUI tools.

How can I get a list of the repositories and apply it to my good OS?

---

### Post by oldfred on 2023-02-11
Does this work once chrooted into install?
cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done

You also should export list of installed apps to make it easy to reinstall.
apt-mark showmanual | sort -u
But that does not include the install on every line.
I have seen several ways to edit file to add install on every line, or add it as part of the install.
Add installed to list of files
sed -i 's/$/\tinstall/' user-installed.list

---

### Post by kogorman-pacbell on 2023-02-11
@oldfred thanks.  Just knowing it's in /etc/apt/sources.list and that plus .d gives me enough to go on, I think.  I will also try your little scripts and report back.

---

### Post by guiverc on 2023-02-11
This won't answer your question  (*I'll leave  you in the very capable hands of OldFred for that*), but you do realize you can re-install Ubuntu **Desktops** system rather easily, non-destructively too.  It notes the packages (*manually installed*) you have, erases system directories (*thus fixing many problems*), then installs from the media you are using & if internet is available attempts to download & install the *manually installed* packages noted earlier if available in repositories. No user file is touched (*unless you formatted*).

You didn't specifically mention Desktop or Server, but you do mention GUI.

I talk about it [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") where the Lubuntu team perform checks for the *Repair Install* type of feature & call it "*Install using existing partition*" (search for "*Install using existing partition*" to find the discussion I've provided). QA testing however do not include any 3rd party packages thus no mention of them is made, & no guarantees exist there (*they can work, or may not work depending on the packages & sources you have added*).

(In the past this install option used to be offered a "*Repair Installation*" option, and the hope is it'll return as available (*in the menus rather than hidden within Something else*) for 23.04 too :P but the option has always been available even after "Repair" was removed long ago by using the "*Something else*"

Mentioned to give you another *last resort* option maybe.

---

### Post by oldfred on 2023-02-11
as guiverc mentions you may be able to repair or do a repair type install.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Or an install were you do not format partition(s). Anything that is part of install will be overwritten, but any unique files you have added should still be there.
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by MAFoElffen on 2023-02-12
Also, if you run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"), it will answer all those questions about the sources list and extended sources.d, as well at user installed packages.

There is a failsafe to try to prevent user from running the report as root for normal use, but I wrote a trap door into it, for Containers and chroots... On where it stops, and prompts not to run it as root... Enter in the passphrase:
```

I am Groot

```
If you enter in that passphrase, it will let you run it as Root.

---

### Post by Impavidus on 2023-02-12
On the other hand, if package management of the old installation is messed up, a dirty reinstall may not fix it, as it will attempt to reinstall the same impossible combination of packages.

After reinstalling, be careful when adding the other repositories back. Maybe one of them caused your broken install.

---

### Post by kogorman-pacbell on 2023-02-12
Well, I had a go at it, and I am not impressed with the result.  None of my additional packages are there -- not even my favorite vim-nox which is from standard repositories.  Since it also clobbers /home and /etc, I have the same re-tailoring and re-installing headaches I had starting with a normal install.  I'll go back to that because I think I'm more clear about what it does and does not do.

I'm still looking for a way to reinstall my list of packages from dpkg --get-selections.  As it stands, nothing gets reinstalled, not even stuff that was installed with the usual `apt install`.  What to so?

---

### Post by MAFoElffen on 2023-02-12
For migrations (Install new, re-install packages, and migrate data), I use the list of user install packages from the 'system-info' script...

Code for that is (extracted):
```

#!bin/bash

function CheckDebianBranch()
{
    # Check if OS is in Debian Branch
    # var debian_branch is global
    if [ -f /etc/debian_version ]
    then
        debian_branch=0
    else
        debian_branch=1
    fi
    # debug "CheckDebianBranch(). Value: $debian_branch" 1
}

function GetUserInstalled()
{
    ## Get a list of User Installed Packages 
    # This only works for Debian Branch...
        
    echo -e "   --- User Installed Package List:"
    # check if Debian Branch. Otherwise 'apt-mark' will not be found...
    if [[ "$debian_branch" == "0" ]]
    then    
        manually_installed=$(mktemp /tmp/ManuallyInstalled-XXXXX)
        default_installed=$(mktemp /tmp/DefaultInstalled-XXXXX)
        user_installed=$(mktemp /tmp/UserInstalled-XXXXX)
        # Use apt-mark to list all packages marked as manually installed. 
        apt-mark showmanual | sort -u > $manually_installed
        # Check to see if defualt installed list exists
        # for prebuilt system images, it does not exist
        if [ -f /var/log/installer/initial-status.gz ]
        then 
            # Get the list of default installed packages at initial installation.
            gzip -dc /var/log/installer/initial-status.gz 2> /dev/null | \
                sed -n 's/^Package: //p' | \
                sort -u > $default_installed
        else 
            touch $default_installed
        fi
        # Use compare, to exclude those defaults that are unique, AND exclude defaults 
        # that are presently marked as manually installed. (Those 'may' have been changed.)  
        comm -23 $manually_installed $default_installed > $user_installed
        # Print the list in two columns
        awk 'NF' $user_installed #\ Removed 2022.03.10 to turn to one column
        #| pr -2T  # You can remove the pr filter on this to keep output in a single column...
        nl # Add newline in report
        # Remove the temporary files
        rm -f $manually_installed
        rm -f $default_installed
        rm -f $user_installed
    else
        echo -e "The system tested is not in the Debian Branch. "
        echo -e "The method written in this script is for Debian Branch conventions."
        nl
    fi
    unset -v manually_installed default_installed user_installed
}

CheckDebianBranch
GetUserInstalled

```

---

