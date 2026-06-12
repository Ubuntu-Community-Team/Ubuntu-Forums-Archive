---
title: "remove duplicate info files and update info directory"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by aleblanc on 2012-08-22
Here is a script for updating removing duplicate info files and updating the info dir file.
This is useful after copying info files from another installation/backup into the info directory.
It searches each of the info directories listed in the INFODIRS variable, and removes any info files that are also found in subdirs of those directories. It then rebuilds the info dir file  (deleting the old one). The user will be prompted before files are deleted, and you will need to type in your password for sudo.
Requires bash version > 4.


```
#!/bin/bash
# Simple script to remove duplicate info files and update the info directories.

# Depends on bash version > 4

# The following variable (INFODIRS) should be set to a list of info file directories to be dealt with.
# Duplicates will be removed from directories that appear earlier in the list before those that appear later.
# and hence later directories get priority over info files when choosing which version to keep.
INFODIRS="/usr/local/share/info /usr/share/info" 

RESETGLOB=`shopt -p | grep globstar` # command to set globstar option to current value
shopt -s globstar # enable recursive globbing (with **)
for dir in $INFODIRS
do
    if [ -d $dir ]; then
        cd $dir
        DUPS=`find $INFODIRS -type f -exec zgrep -l START-INFO-DIR-ENTRY {} \;|xargs -L 1 basename|sort|uniq -c|grep -v " 1 "|awk '{print $2}'|tr '\n' ' '`
        if [ $DUPS ]; then
            echo "The following info files have duplicates: $DUPS"
            read -p "Do you want to remove those duplicates from the current dir? " -r
            if [[ $REPLY =~ ^[Yy]$ ]]
            then
                sudo rm $DUPS
            fi
        fi
        ALLINFOS=`find $INFODIRS -type f -exec zgrep -l START-INFO-DIR-ENTRY {} \;`
        # recreate the info directory
        sudo rm dir
        for f in $ALLINFOS; do sudo install-info $f dir 2>/dev/null; done
    fi
done
eval $RESETGLOB # reset globstar option to it's previous value

```

---

