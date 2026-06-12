---
title: "Need help downgrading to Grub 1"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-08
i think that after three days of trying to install ubuntu 10.04 properly that it's not working out grub 2 just doesn't work i need help downgrading to grub 1 and make sure that it would recognize my windows 7 installtion.
 
my ubuntu partition is sda1 on sda but this is not the first HD thet is set in bios the first is the one ubuntu recognize as sdb and my windows 7 partition is sdb1. 
 
now how can i mount from live cd and to what remove grub 2 from there then install grub 1?
 
in a nutshell so to speak i need to get this os to work in any way possible or completly forget about it and stay with 7 or install fedora and etc.
 
thanks in advance.

---

### Post by Enigmapond on 2010-02-08
This thread may be useful...

[http://ubuntuforums.org/showthread.php?t=1325901](http://ubuntuforums.org/showthread.php?t=1325901)

---

### Post by aviramof on 2010-02-08
doesn't work and i'm tierd of grub 2 attempts i just want grub 1 and that it.

thanks in advance.

---

### Post by Enigmapond on 2010-02-08
What doesn't work? The link I gave you included instructions on how to boot from Live cd and get Grub back...I know it works...I did it....read the whole thread.

---

### Post by aviramof on 2010-02-08
what part of this thread:
 
**sudo bash**
**mount /dev/sda1 /mnt**
**mount --bind /dev /mnt/dev**
**chroot /mnt**
**grub-install /dev/sda**
**update-grub**
 
**maybe **mount --bind /dev /mnt/dev with **mount --bind /dev /mnt/dev**

---

### Post by phenest on 2010-02-08
> **aviramof said:**
> my ubuntu partition is sda1 on sda but this is not the first HD thet is set in bios the first is the one ubuntu recognize as sdb and my windows 7 partition is sdb1. 
 
now how can i mount from live cd and to what remove grub 2 from there then install grub 1?

So you need to install grub2 on the drive with Windows 7 instead? I don't see how installing grub 1 will change anything.

---

### Post by phenest on 2010-02-08
> **aviramof said:**
> what part of this thread:
 
**sudo bash**
**mount /dev/sda1 /mnt**
**mount --bind /dev /mnt/dev**
**chroot /mnt**
**grub-install /dev/sda**
**update-grub**
 
**maybe **mount --bind /dev /mnt/dev with **mount --bind /dev /mnt/dev**

Except it should be 'grub-install /dev/sdb'?

---

### Post by Enigmapond on 2010-02-08
This whole section will get you back your original grub...

```
Start your computer from a Ubuntu 9.10 LiveCD and select Try Ubuntu  without any change to your computer.

When the start is finshed, open Gparted (System -> Administration  -> GParted) and try to locate the Ubuntu partition (probably a File  System ext3 or ext4). I will suppose that this partitios is /dev/sda1.  If no, please, chage it with the correct device. 

Open a terminal (Applications -> Accessories -> Terminal)

Type the following commands:

sudo bash                     #the system will ask for your password
mount /dev/sda1 /mnt   #May be your device is not /dev/sda1
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda     #no number here
update-grub
```

---

### Post by aviramof on 2010-02-08
> **phenest said:**
> So you need to install grub2 on the drive with Windows 7 instead? I don't see how installing grub 1 will change anything.

and how do i do this?
because so far i didn't had much luck doing that.

and this is what i get
```
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

```and this is what i get from set
```
    return 0
}
_tcpdump () 
{ 
    local cur prev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -@(r|w|F))
            _filedir;
            return 0
        ;;
        -i)
            _available_interfaces -a;
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-a -d -e -f -l -n -N -O -p \
            -q -R -S -t -u -v -x -C -F -i -m -r -s -T -w -E' -- "$cur" ));
    fi
}
_ufw () 
{ 
    cur=${COMP_WORDS[COMP_CWORD]};
    prev=${COMP_WORDS[COMP_CWORD-1]};
    if [ $COMP_CWORD -eq 1 ]; then
        COMPREPLY=($( compgen -W "$(_ufw_commands)" $cur ));
    else
        if [ $COMP_CWORD -eq 2 ]; then
            case "$prev" in 
                app)
                    COMPREPLY=($( compgen -W "$(_ufw_app_commands)" $cur ))
                ;;
                status)
                    COMPREPLY=($( compgen -W "$(_ufw_status_commands)" $cur ))
                ;;
                delete)
                    COMPREPLY=($( compgen -W "$(_ufw_rule_commands)" $cur ))
                ;;
                logging)
                    COMPREPLY=($( compgen -W "$(_ufw_logging_commands)" $cur ))
                ;;
                show)
                    COMPREPLY=($( compgen -W "$(_ufw_show_commands)" $cur ))
                ;;
                default)
                    COMPREPLY=($( compgen -W "$(_ufw_default_commands)" $cur ))
                ;;
            esac;
        fi;
    fi
}
_ufw_app_commands () 
{ 
    ufw --help | sed -e '1,/^Application profile commands:/d' -e '/^ [^ ]/!d' -e 's/[ \t]\+app[ \t]\+\([a-z|]\+\)[ \t]\+.*/\1/g'
}
_ufw_commands () 
{ 
    commands=$(ufw --help | sed -e '1,/^Commands:/d' -e '/^Application profile commands:/Q' -e 's/^[ \t]\+\([a-z|]\+\)[ \t]\+.*/\1/g' -e 's/|/ /g' | uniq);
    echo "$commands app"
}
_ufw_default_commands () 
{ 
    echo "allow deny reject"
}
_ufw_logging_commands () 
{ 
    echo "off on low medium high full"
}
_ufw_rule_commands () 
{ 
    echo "`_ufw_default_commands` limit"
}
_ufw_show_commands () 
{ 
    echo "raw"
}
_ufw_status_commands () 
{ 
    echo "numbered verbose"
}
_uids () 
{ 
    if type getent &>/dev/null; then
        COMPREPLY=($( compgen -W '$( getent passwd | cut -d: -f3 )' -- "$cur" ));
    else
        if type perl &>/dev/null; then
            COMPREPLY=($( compgen -W '$( perl -e '"'"'while (($uid) = (getpwent)[2]) { print $uid . "\n" }'"'"' )' -- "$cur" ));
        else
            COMPREPLY=($( compgen -W '$( cut -d: -f3 /etc/passwd )' -- "$cur" ));
        fi;
    fi
}
_umount () 
{ 
    local cur IFS='
';
    COMPREPLY=();
    cur=`_get_cword`;
    COMPREPLY=($( compgen -W '$( mount | cut -d" " -f 3 )' -- "$cur" ));
    return 0
}
_update_alternatives () 
{ 
    local cur prev mode args i;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        --@(altdir|admindir))
            _filedir -d;
            return 0
        ;;
        --@(help|version))
            return 0
        ;;
    esac;
    for ((i=1; i < COMP_CWORD; i++ ))
    do
        if [[ "${COMP_WORDS[i]}" == --@(install|remove|auto|display|config|remove-all) ]]; then
            mode=${COMP_WORDS[i]};
            args=$(($COMP_CWORD - i));
            break;
        fi;
    done;
    case $mode in 
        --install)
            case $args in 
                1)
                    _filedir
                ;;
                2)
                    _installed_alternatives
                ;;
                3)
                    _filedir
                ;;
            esac
        ;;
        --remove)
            case $args in 
                1)
                    _installed_alternatives
                ;;
                2)
                    _filedir
                ;;
            esac
        ;;
        --auto)
            _installed_alternatives
        ;;
        --remove-all)
            _installed_alternatives
        ;;
        --display)
            _installed_alternatives
        ;;
        --config)
            _installed_alternatives
        ;;
        *)
            COMPREPLY=($( compgen -W '--verbose --quiet --help --version \
                   --altdir --admindir' -- "$cur" ) $( compgen -W '--install --remove --auto --display \
                   --config' -- "$cur" ))
        ;;
    esac
}
_update_rc_d () 
{ 
    local cur prev sysvdir services options valid_options;
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;
    services=($(echo $sysvdir/!(README*|*.sh|*.dpkg*|*.rpm@(orig|new|save))));
    services=(${services[@]#$sysvdir/});
    options=(-f -n);
    if [[ $COMP_CWORD -eq 1 || "$prev" == -* ]]; then
        valid_options=($(         echo "${COMP_WORDS[@]} ${options[@]}"         | tr " " "\n"         | sed -ne "/$( echo "${options[@]}" | sed "s/ /\\|/g" )/p"         | sort | uniq -u         ));
        COMPREPLY=($( compgen -W '${options[@]} ${services[@]}'         -X '$( echo ${COMP_WORDS[@]} | tr " " "|" )' -- "$cur" ));
    else
        if [[ "$prev" == ?($( echo ${services[@]} | tr " " "|" )) ]]; then
            COMPREPLY=($( compgen -W 'remove defaults start stop' -- "$cur" ));
        else
            if [[ "$prev" == defaults && "$cur" == [0-9] ]]; then
                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
            else
                if [[ "$prev" == defaults && "$cur" == [sk]?([0-9]) ]]; then
                    COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
                else
                    if [[ "$prev" == defaults && -z "$cur" ]]; then
                        COMPREPLY=(0 1 2 3 4 5 6 7 8 9 s k);
                    else
                        if [[ "$prev" == ?(start|stop) ]]; then
                            if [[ "$cur" == [0-9] || -z "$cur" ]]; then
                                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
                            else
                                if [[ "$cur" == [0-9][0-9] ]]; then
                                    COMPREPLY=($cur);
                                else
                                    COMPREPLY=();
                                fi;
                            fi;
                        else
                            if [[ "$prev" == ?([0-9][0-9]|[0-6S]) ]]; then
                                if [[ -z "$cur" ]]; then
                                    if [[ $prev == [0-9][0-9] ]]; then
                                        COMPREPLY=(0 1 2 3 4 5 6 S);
                                    else
                                        COMPREPLY=(0 1 2 3 4 5 6 S .);
                                    fi;
                                else
                                    if [[ "$cur" == [0-6S.] ]]; then
                                        COMPREPLY=($cur);
                                    else
                                        COMPREPLY=();
                                    fi;
                                fi;
                            else
                                if [[ "$prev" == "." ]]; then
                                    COMPREPLY=($(compgen -W "start stop" -- "$cur"));
                                else
                                    COMPREPLY=();
                                fi;
                            fi;
                        fi;
                    fi;
                fi;
            fi;
        fi;
    fi;
    return 0
}
_usb_ids () 
{ 
    COMPREPLY=(${COMPREPLY[@]:-} $( compgen -W     "$( PATH="$PATH:/sbin" lsusb | awk '{print $6}' )" -- "$cur" ))
}
_user_at_host () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    if [[ $cur == *@* ]]; then
        _known_hosts_real "$cur";
    else
        COMPREPLY=($( compgen -u -- "$cur" ));
    fi;
    return 0
}
_useradd () 
{ 
    local cur prev split=false;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    _split_longopt && split=true;
    case "$prev" in 
        -c | --comment | -h | --help | -e | --expiredate | -f | --inactive | -k | --key | -p | --password | -u | --uid | -Z | --selinux-user)
            return 0
        ;;
        -b | --base-dir | -d | --home | -k | --skel)
            _filedir -d;
            return 0
        ;;
        -g | --gid)
            _gids;
            [ -n "$bash205" ] && COMPREPLY=("${COMPREPLY[@]}" $( compgen -g ));
            COMPREPLY=($( compgen -W '${COMPREPLY[@]}' -- "$cur" ));
            return 0
        ;;
        -G | --groups)
            [ -n "$bash205" ] && COMPREPLY=($( compgen -g -- "$cur" ));
            return 0
        ;;
        -s | --shell)
            _shells;
            return 0
        ;;
    esac;
    $split && return 0;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-b --base-dir -c --comment -d --home\
            -D --defaults -e --expiredate -f --inactive -g --gid \
            -G --groups -h --help -k --skel -K --key -l -M \
            -m --create-home -N --no-user-group -o --non-unique \
            -p --password -r --system -s --shell -u --uid \
            -U --user-group -Z --selinux-user' -- "$cur" ));
        return 0;
    fi
}
_userdel () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-f --force -h --help -r --remove'             -- "$cur" ));
        return 0;
    fi;
    COMPREPLY=($( compgen -u -- "$cur" ))
}
_usergroup () 
{ 
    local IFS='
';
    cur=${cur//\\\\ / };
    if [[ $cur = *@(\\:|.)* ]] && [ -n "$bash205" ]; then
        user=${cur%%*([^:.])};
        COMPREPLY=($(compgen -P ${user/\\\\} -g -- ${cur##*[.:]}));
    else
        if [[ $cur = *:* ]] && [ -n "$bash205" ]; then
            COMPREPLY=($( compgen -g -- ${cur##*[.:]} ));
        else
            COMPREPLY=($( compgen -S : -u -- "$cur" ));
        fi;
    fi
}
_usermod () 
{ 
    local cur prev split=false;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    _split_longopt && split=true;
    case "$prev" in 
        -c | --comment | -d | --home | -e | --expiredate | -f | --inactive | -h | --help | -l | --login | -p | --password | -u | --uid | -Z | --selinux-user)
            return 0
        ;;
        -g | --gid)
            _gids;
            [ -n "$bash205" ] && COMPREPLY=("${COMPREPLY[@]}" $( compgen -g ));
            COMPREPLY=($( compgen -W '${COMPREPLY[@]}' -- "$cur" ));
            return 0
        ;;
        -G | --groups)
            [ -n "$bash205" ] && COMPREPLY=($( compgen -g -- "$cur" ));
            return 0
        ;;
        -s | --shell)
            _shells;
            return 0
        ;;
    esac;
    $split && return 0;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-a --append -c --comment -d --home \
            -e --expiredate -f --inactive -g --gid -G --groups \
            -h --help -l --login -L --lock -o --non-unique \
            -p --password -s --shell -u --uid -U --unlock \
            -Z --selinux-user' -- "$cur" ));
        return 0;
    fi;
    COMPREPLY=($( compgen -u -- "$cur" ))
}
_vipw () 
{ 
    local cur prev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -h | --help)
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-g --group -h --help -p --passwd \
            -q --quiet -s --shadow' -- "$cur" ));
        return 0;
    fi
}
_xhost () 
{ 
    local cur=`_get_cword`;
    case "$cur" in 
        +*)
            _known_hosts_real -p+ "${cur:1}"
        ;;
        -*)
            _known_hosts_real -p- "${cur:1}"
        ;;
        *)
            _known_hosts_real "$cur"
        ;;
    esac;
    return 0
}
_xmllint () 
{ 
    local cur prev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -o | --output)
            _filedir;
            return 0
        ;;
        --path | --dtdvalidfpi | --maxmem | --encode | --pattern)
            return 0
        ;;
        --dtdvalid)
            _filedir dtd;
            return 0
        ;;
        --relaxng)
            _filedir rng;
            return 0
        ;;
        --schema)
            _filedir xsd;
            return 0
        ;;
        --schematron)
            _filedir sch;
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '$( xmllint --help 2>&1 | \
            sed -ne "s/^[[:space:]]*\(--[^[:space:]:]*\).*/\1/p" ) \
            -o' -- "$cur" ));
        return 0;
    fi;
    _filedir '@(*ml|htm|svg)'
}
_xrandr () 
{ 
    local cur prev output modes;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        --output)
            local outputs=$(xrandr|grep 'connected'|awk '{print $1}');
            COMPREPLY=($(compgen -W "$outputs" -- "$cur"));
            return 0
        ;;
        --mode)
            for ((i = 1; i < COMP_CWORD; i++ ))
            do
                if [[ "${COMP_WORDS[i]}" == "--output" ]]; then
                    output=${COMP_WORDS[i+1]};
                    break;
                fi;
            done;
            modes=$(xrandr|sed -e "1,/$output/ d"                 -e "/connected/,$ d"|awk '{print $1}');
            COMPREPLY=($( compgen -W "$modes" -- "$cur"));
            return 0
        ;;
    esac;
    case "$cur" in 
        *)
            COMPREPLY=($(compgen -W '-d -display -help -o \
                    --orientation -q --query -s --size\
                    -r --rate -v --version -x -y --screen \
                    --verbose --dryrun --prop --fb \
                    --fbmm --dpi --output --auto --mode \
                    --preferred --pos --reflect --rotate \
                    --left-of --right-of --above --below \
                    --same-as --set --off --crtc --newmode \
                    --rmmode --addmode --delmode' -- "$cur"));
            return 0
        ;;
    esac;
    return 0
}
command_not_found_handle () 
{ 
    if [ -x /usr/lib/command-not-found ]; then
        /usr/bin/python /usr/lib/command-not-found -- $1;
        return $?;
    else
        return 127;
    fi
}
dequote () 
{ 
    eval echo "$1" 2> /dev/null
}
quote () 
{ 
    echo \'${1//\'/\'\\\'\'}\'
}
quote_readline () 
{ 
    if [ -n "$bash4" ]; then
        echo "${1}";
        return;
    fi;
    local t="${1//\\/\\\\}";
    echo \'${t//\'/\'\\\'\'}\'
}
```

---

### Post by aviramof on 2010-02-08
i used sudo aptitude install grub-pc from this link
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

and nothing more and now it enter the os now how can i add the rest of the things to the boot especily windows 7?

thanks in advance.

---

### Post by kansasnoob on 2010-02-08
Just as an FYI:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

In appendix #2 I also explain how to go from legacy grub back to grub2.

---

### Post by aviramof on 2010-02-08
wrong thread:
[http://ubuntuforums.org/showthread.php?t=1401587&page=2](http://ubuntuforums.org/showthread.php?t=1401587&page=2)

---

