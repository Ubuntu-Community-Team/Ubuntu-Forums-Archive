---
title: "Migration to another PC - removing grub and &quot;disk UUID not ready&quot;"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2015-12-25
Hi there,

I have just cloned (via dd - long story) the Ubuntu partitions of my 'buntu/win10 dual boot install onto a fresh SSD to use in another PC.

The system boots and works nice, but there are delays in the boot process.

Grub still shows a boot menu (incl an option for the old Win10 which I don't have on this SSD). I'm a bit scared to just uninstall it grub - I can't see any tutorials online to go from dual to single boot.

Also, I think the system is still looking for the win10, or perhaps waiting for my swap partition as that has a similar UUID to the one in the message (808cb at the end) because it delays startup and shows the message "disk UUID XXXX is not ready..." briefly.

I have tried boot-repair and corrected the UUID for my swap partition in etc/fstab, but the issues are still there. 

The output of blkid is:

```

/dev/sda1: UUID="dc88635b-e694-4683-9e79-63b659d808cb" TYPE="swap" /dev/sda5: UUID="468bfcd7-cb38-449f-9e63-6d40a484f648" TYPE="ext4" 
/dev/sda6: UUID="119017f8-4da1-4475-9bc7-284fe2ac5048" TYPE="ext2" 
/dev/zram0: UUID="8629574e-72f9-452a-b248-c62a44031950" TYPE="swap" 
/dev/zram1: UUID="813be9ea-82d6-4ccc-9551-dbcdcbb04b34" TYPE="swap"

```

my etc/fstab is:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 /               ext4    defaults  0    $
# /home was on /dev/sda6 during installation
UUID=119017f8-4da1-4475-9bc7-284fe2ac5048 /home           ext2    defaults       $
# swap was on /dev/sda7 during installation
UUID="dc88635b-e694-4683-9e79-63b659d808cb none            swap    sw            $

```

The output from boot-repair is here:
paste.ubuntu.com/14208701

I'm sure I'm just missing something simple. Any ideas?

---

### Post by grahammechanical on 2015-12-25
In Ubuntu and its family members there are two commands that are useful to know in regard to Grub. This command will reconfigure the Grub boot menu. And it should remove the entry for Windows 10 from the Grub boot menu.

```
sudo update-grub
```

It will produces a printout that identifies the operating systems that it has found and which will appear in the Grub boot menu. The other I offer for completeness. It reinstalls Grub to the hard disk but we have to be specific as regards hard drives. A single hard drive will be sda. 2 hard drives will be sda & sdb. We need to be careful where we install Grub.

So, with a single hard drive (sda) & Ubuntu installed on sda & Ubuntu loaded, we run

```
sudo grub-install /dev/sda
```

If we are running Ubuntu from sdb we change the command accordingly. If the issue is with labels in the UEFI boot system, then that is a different matter and about which I have no practical experience.

Regards.

---

### Post by steve234 on 2015-12-25
Didn't work at all - the update threw an error:

```

sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported

```

```

sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 352
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

```

---

### Post by yancek on 2015-12-25
So what does line 352 of the grub.cfg file show?

Check the /etc/default/grub file or post it here for review.

---

### Post by steve234 on 2015-12-25
apologies thought I had posted that - I don't think it's 352 lines long!

/etc/default/grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by ubfan1 on 2015-12-25
I think that error was line 352 of /boot/grub/grub.cfg.new , the newly generated grub.cfg file.  You can nunmber the lines with the -n switch of cat, e.g.:
cat -n /boot/grub/grub.cfg.new

---

### Post by steve234 on 2015-12-25
thanks UBfan that switch is a good tip. Yes I had a look at /boot/grub/grub.cfg.new  but it was all full of win stuff just like the "old" /boot/grub/grub.cfg

Contents of /boot/grub/grub.cfg.new are:

```

1    #
     2    # DO NOT EDIT THIS FILE
     3    #
     4    # It is automatically generated by grub-mkconfig using templates
     5    # from /etc/grub.d and settings from /etc/default/grub
     6    #
     7    
     8    ### BEGIN /etc/grub.d/00_header ###
     9    if [ -s $prefix/grubenv ]; then
    10      set have_grubenv=true
    11      load_env
    12    fi
    13    if [ "${next_entry}" ] ; then
    14       set default="${next_entry}"
    15       set next_entry=
    16       save_env next_entry
    17       set boot_once=true
    18    else
    19       set default="0"
    20    fi
    21    
    22    if [ x"${feature_menuentry_id}" = xy ]; then
    23      menuentry_id_option="--id"
    24    else
    25      menuentry_id_option=""
    26    fi
    27    
    28    export menuentry_id_option
    29    
    30    if [ "${prev_saved_entry}" ]; then
    31      set saved_entry="${prev_saved_entry}"
    32      save_env saved_entry
    33      set prev_saved_entry=
    34      save_env prev_saved_entry
    35      set boot_once=true
    36    fi
    37    
    38    function savedefault {
    39      if [ -z "${boot_once}" ]; then
    40        saved_entry="${chosen}"
    41        save_env saved_entry
    42      fi
    43    }
    44    function recordfail {
    45      set recordfail=1
    46      if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
    47    }
    48    function load_video {
    49      if [ x$feature_all_video_module = xy ]; then
    50        insmod all_video
    51      else
    52        insmod efi_gop
    53        insmod efi_uga
    54        insmod ieee1275_fb
    55        insmod vbe
    56        insmod vga
    57        insmod video_bochs
    58        insmod video_cirrus
    59      fi
    60    }
    61    
    62    if [ x$feature_default_font_path = xy ] ; then
    63       font=unicode
    64    else
    65    insmod part_msdos
    66    insmod ext2
    67    set root='hd0,msdos5'
    68    if [ x$feature_platform_search_hint = xy ]; then
    69      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
    70    else
    71      search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
    72    fi
    73        font="/usr/share/grub/unicode.pf2"
    74    fi
    75    
    76    if loadfont $font ; then
    77      set gfxmode=auto
    78      load_video
    79      insmod gfxterm
    80      set locale_dir=$prefix/locale
    81      set lang=en_GB
    82      insmod gettext
    83    fi
    84    terminal_output gfxterm
    85    if [ "${recordfail}" = 1 ] ; then
    86      set timeout=30
    87    else
    88      if [ x$feature_timeout_style = xy ] ; then
    89        set timeout_style=menu
    90        set timeout=10
    91      # Fallback normal timeout code in case the timeout_style feature is
    92      # unavailable.
    93      else
    94        set timeout=10
    95      fi
    96    fi
    97    ### END /etc/grub.d/00_header ###
    98    
    99    ### BEGIN /etc/grub.d/05_debian_theme ###
   100    set menu_color_normal=white/black
   101    set menu_color_highlight=black/light-gray
   102    ### END /etc/grub.d/05_debian_theme ###
   103    
   104    ### BEGIN /etc/grub.d/10_linux ###
   105    function gfxmode {
   106        set gfxpayload="${1}"
   107        if [ "${1}" = "keep" ]; then
   108            set vt_handoff=vt.handoff=7
   109        else
   110            set vt_handoff=
   111        fi
   112    }
   113    if [ "${recordfail}" != 1 ]; then
   114      if [ -e ${prefix}/gfxblacklist.txt ]; then
   115        if hwmatch ${prefix}/gfxblacklist.txt 3; then
   116          if [ ${match} = 0 ]; then
   117            set linux_gfx_mode=keep
   118          else
   119            set linux_gfx_mode=text
   120          fi
   121        else
   122          set linux_gfx_mode=text
   123        fi
   124      else
   125        set linux_gfx_mode=keep
   126      fi
   127    else
   128      set linux_gfx_mode=text
   129    fi
   130    export linux_gfx_mode
   131    menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   132        recordfail
   133        load_video
   134        gfxmode $linux_gfx_mode
   135        insmod gzio
   136        insmod part_msdos
   137        insmod ext2
   138        set root='hd0,msdos5'
   139        if [ x$feature_platform_search_hint = xy ]; then
   140          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   141        else
   142          search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   143        fi
   144        linux    /boot/vmlinuz-3.19.0-39-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro  quiet splash $vt_handoff
   145        initrd    /boot/initrd.img-3.19.0-39-generic
   146    }
   147    submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   148        menuentry 'Ubuntu, with Linux 3.19.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-39-generic-advanced-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   149            recordfail
   150            load_video
   151            gfxmode $linux_gfx_mode
   152            insmod gzio
   153            insmod part_msdos
   154            insmod ext2
   155            set root='hd0,msdos5'
   156            if [ x$feature_platform_search_hint = xy ]; then
   157              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   158            else
   159              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   160            fi
   161            echo    'Loading Linux 3.19.0-39-generic ...'
   162            linux    /boot/vmlinuz-3.19.0-39-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro  quiet splash $vt_handoff
   163            echo    'Loading initial ramdisk ...'
   164            initrd    /boot/initrd.img-3.19.0-39-generic
   165        }
   166        menuentry 'Ubuntu, with Linux 3.19.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-39-generic-recovery-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   167            recordfail
   168            load_video
   169            insmod gzio
   170            insmod part_msdos
   171            insmod ext2
   172            set root='hd0,msdos5'
   173            if [ x$feature_platform_search_hint = xy ]; then
   174              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   175            else
   176              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   177            fi
   178            echo    'Loading Linux 3.19.0-39-generic ...'
   179            linux    /boot/vmlinuz-3.19.0-39-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro recovery nomodeset 
   180            echo    'Loading initial ramdisk ...'
   181            initrd    /boot/initrd.img-3.19.0-39-generic
   182        }
   183        menuentry 'Ubuntu, with Linux 3.19.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-advanced-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   184            recordfail
   185            load_video
   186            gfxmode $linux_gfx_mode
   187            insmod gzio
   188            insmod part_msdos
   189            insmod ext2
   190            set root='hd0,msdos5'
   191            if [ x$feature_platform_search_hint = xy ]; then
   192              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   193            else
   194              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   195            fi
   196            echo    'Loading Linux 3.19.0-33-generic ...'
   197            linux    /boot/vmlinuz-3.19.0-33-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro  quiet splash $vt_handoff
   198            echo    'Loading initial ramdisk ...'
   199            initrd    /boot/initrd.img-3.19.0-33-generic
   200        }
   201        menuentry 'Ubuntu, with Linux 3.19.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-recovery-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   202            recordfail
   203            load_video
   204            insmod gzio
   205            insmod part_msdos
   206            insmod ext2
   207            set root='hd0,msdos5'
   208            if [ x$feature_platform_search_hint = xy ]; then
   209              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   210            else
   211              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   212            fi
   213            echo    'Loading Linux 3.19.0-33-generic ...'
   214            linux    /boot/vmlinuz-3.19.0-33-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro recovery nomodeset 
   215            echo    'Loading initial ramdisk ...'
   216            initrd    /boot/initrd.img-3.19.0-33-generic
   217        }
   218        menuentry 'Ubuntu, with Linux 3.19.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-32-generic-advanced-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   219            recordfail
   220            load_video
   221            gfxmode $linux_gfx_mode
   222            insmod gzio
   223            insmod part_msdos
   224            insmod ext2
   225            set root='hd0,msdos5'
   226            if [ x$feature_platform_search_hint = xy ]; then
   227              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   228            else
   229              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   230            fi
   231            echo    'Loading Linux 3.19.0-32-generic ...'
   232            linux    /boot/vmlinuz-3.19.0-32-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro  quiet splash $vt_handoff
   233            echo    'Loading initial ramdisk ...'
   234            initrd    /boot/initrd.img-3.19.0-32-generic
   235        }
   236        menuentry 'Ubuntu, with Linux 3.19.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-32-generic-recovery-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   237            recordfail
   238            load_video
   239            insmod gzio
   240            insmod part_msdos
   241            insmod ext2
   242            set root='hd0,msdos5'
   243            if [ x$feature_platform_search_hint = xy ]; then
   244              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   245            else
   246              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   247            fi
   248            echo    'Loading Linux 3.19.0-32-generic ...'
   249            linux    /boot/vmlinuz-3.19.0-32-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro recovery nomodeset 
   250            echo    'Loading initial ramdisk ...'
   251            initrd    /boot/initrd.img-3.19.0-32-generic
   252        }
   253        menuentry 'Ubuntu, with Linux 3.19.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-31-generic-advanced-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   254            recordfail
   255            load_video
   256            gfxmode $linux_gfx_mode
   257            insmod gzio
   258            insmod part_msdos
   259            insmod ext2
   260            set root='hd0,msdos5'
   261            if [ x$feature_platform_search_hint = xy ]; then
   262              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   263            else
   264              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   265            fi
   266            echo    'Loading Linux 3.19.0-31-generic ...'
   267            linux    /boot/vmlinuz-3.19.0-31-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro  quiet splash $vt_handoff
   268            echo    'Loading initial ramdisk ...'
   269            initrd    /boot/initrd.img-3.19.0-31-generic
   270        }
   271        menuentry 'Ubuntu, with Linux 3.19.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-31-generic-recovery-468bfcd7-cb38-449f-9e63-6d40a484f648' {
   272            recordfail
   273            load_video
   274            insmod gzio
   275            insmod part_msdos
   276            insmod ext2
   277            set root='hd0,msdos5'
   278            if [ x$feature_platform_search_hint = xy ]; then
   279              search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   280            else
   281              search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   282            fi
   283            echo    'Loading Linux 3.19.0-31-generic ...'
   284            linux    /boot/vmlinuz-3.19.0-31-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro recovery nomodeset 
   285            echo    'Loading initial ramdisk ...'
   286            initrd    /boot/initrd.img-3.19.0-31-generic
   287        }
   288    }
   289    
   290    ### END /etc/grub.d/10_linux ###
   291    
   292    ### BEGIN /etc/grub.d/20_linux_xen ###
   293    
   294    ### END /etc/grub.d/20_linux_xen ###
   295    
   296    ### BEGIN /etc/grub.d/20_memtest86+ ###
   297    menuentry 'Memory test (memtest86+)' {
   298        insmod part_msdos
   299        insmod ext2
   300        set root='hd0,msdos5'
   301        if [ x$feature_platform_search_hint = xy ]; then
   302          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   303        else
   304          search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   305        fi
   306        knetbsd    /boot/memtest86+.elf
   307    }
   308    menuentry 'Memory test (memtest86+, serial console 115200)' {
   309        insmod part_msdos
   310        insmod ext2
   311        set root='hd0,msdos5'
   312        if [ x$feature_platform_search_hint = xy ]; then
   313          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  468bfcd7-cb38-449f-9e63-6d40a484f648
   314        else
   315          search --no-floppy --fs-uuid --set=root 468bfcd7-cb38-449f-9e63-6d40a484f648
   316        fi
   317        linux16    /boot/memtest86+.bin console=ttyS0,115200n8
   318    }
   319    ### END /etc/grub.d/20_memtest86+ ###
   320    
   321    ### BEGIN /etc/grub.d/30_os-prober ###
   322    ### END /etc/grub.d/30_os-prober ###
   323    
   324    ### BEGIN /etc/grub.d/30_uefi-firmware ###
   325    ### END /etc/grub.d/30_uefi-firmware ###
   326    
   327    ### BEGIN /etc/grub.d/40_custom ###
   328    # This file provides an easy way to add custom menu entries.  Simply type the
   329    # menu entries you want to add after this comment.  Be careful not to change
   330    # the 'exec tail' line above.
   331    'Windows 10' {
   332    set root='(hd0,msdos2)'
   333    chainloader +1
   334    }
   335    ### END /etc/grub.d/40_custom ###
   336    
   337    ### BEGIN /etc/grub.d/40_custom.save ###
   338    # This file provides an easy way to add custom menu entries.  Simply type the
   339    # menu entries you want to add after this comment.  Be careful not to change
   340    # the 'exec tail' line above.
   341    'Windows 10 Technical Preview' {
   342    set root='(hd0,msdos2)'
   343    chainloader +
   344    ### END /etc/grub.d/40_custom.save ###
   345    
   346    ### BEGIN /etc/grub.d/41_custom ###
   347    if [ -f  ${config_directory}/custom.cfg ]; then
   348      source ${config_directory}/custom.cfg
   349    elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
   350      source $prefix/custom.cfg;
   351    fi
   352    ### END /etc/grub.d/41_custom ###

```

---

### Post by oldfred on 2015-12-25
Your Boot-Repair shows the Windows 10 entry with the ending }, but the one you posted above does not show it? So did it get deleted from 40_custom?

Also if now an SSD, you need to convert from ext2 to ext4. I understand ext2 does not support trim. Normally ext2 is only used for smaller partitions or a /boot that may be mostly read, with only few  writes.

---

### Post by steve234 on 2015-12-26
Thanks oldfred, I've now converted to ext4

I have also deleted the custom win10 entry from 40_custom - but the update-grub problem remains.

I think we are getting a bit off piste here - all I want to acheive is to boot straight to the lubuntu spash screen (i.e not seeing or wwating for the Grub menu) - I've seen that the timeout can be set to 0 but that is a bodge?

---

### Post by steve234 on 2015-12-26
I've fixed this now - I copied my 40_custom (minus windows) over 40_custom.save and the grub update worked.  I can now boot without the menu.

Thanks for all your help and other tips, especially for cat and the ext FS for an SSD - I've learned a lot

---

### Post by ubfan1 on 2015-12-26
Looked like a missing } in that section, and the script ran off the end looking for it, hence the 352 line (last line).

---

