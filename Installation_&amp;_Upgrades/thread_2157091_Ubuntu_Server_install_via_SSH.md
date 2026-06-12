---
title: "Ubuntu Server install via SSH"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by Treekodar on 2013-06-24
Hello,

I would like to install Ubuntu Server 13.04 via SSH. The situation is as follows:
I have a headless NAS box at home which _can_ boot from DVD. Now, I've successfully made an ISO which automatically installs the entire Ubuntu Server 13.04 OS onto the NAS, but I would like to try it a bit differently: I would like to create a bootable DVD which brings me straight to an SSH 'environment' where I can continue the installation from a remote (local) computer. I managed to do that with OpenSUSE, but have yet to figure out how to do it in Ubuntu. There will be no keyboard/mouse attached to the NAS, ever.

I know it's possible, but I would like directions on how to do it. 

Cheers,

---

### Post by Lars Noodén on 2013-06-24
I've only looked a little at this and not gotten around to trying it.  I think what you need is the Alternate disc and then to choose F6-Expert mode.  Then when you get to "Load installer components from CD" you can choose "network-console" to continue the installation via SSH.

If instead you need to do that automatically, I think the way forward would be to configure your own preseed.

---

### Post by Treekodar on 2013-06-24
Configuring a preseed does sound like the only proper option at the moment.

---

### Post by Lars Noodén on 2013-06-24
Two tips about developing your own preseed.  

One is to test your new DVD or CD image in a VM like VirtualBox.  That method might have the shortest iteration cycles.  

Another, if you have to test on real, physical hardware is to set up a web server on your LAN to serve the preseed.cfg file.  Then burn a DVD RW or CD RW and point it to the LAN's web server.  Then you don't need to spend any time re-burning the disc only change the preseed file and reboot.  

Either way, when you are 'done' burn to a DVD RW or CD RW because the first 10 or so will turn out to be wrong somehow.  ;)

---

### Post by Treekodar on 2013-06-24
> **Lars Noodén said:**
> Two tips about developing your own preseed.  

One is to test your new DVD or CD image in a VM like VirtualBox.  That method might have the shortest iteration cycles.  

Indeed, that's why I'm doing it in VMWare.


> **Lars Noodén said:**
> 
Another, if you have to test on real, physical hardware is to set up a  web server on your LAN to serve the preseed.cfg file.  Then burn a DVD  RW or CD RW and point it to the LAN's web server.  Then you don't need  to spend any time re-burning the disc only change the preseed file and  reboot.  
 
This is the part I'm not safe about. I'm unsure how to setup a web server (all I have is my NAS, a laptop and my Desktop computer running Win8). One way would be to make my Ubuntu laptop a web server I suppose. I'll try googling around.

---

### Post by Lars Noodén on 2013-06-24
The web server is very easy to set up on your Ubuntu lapttop.  Just install the package Apache2 or nginx then put the files you want to serve in /var/www.  When you are done, you can uninstall the package.

---

### Post by Treekodar on 2013-06-24
I'll try that when I get home. I sincerely thank you for your help O:)

---

### Post by Treekodar on 2013-06-24
Following this guide here: [https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole) I seem to get stuck at a couple of points. 
First my preseed file is at 127.0.1.1 which is pretty problematic when it comes to my own network. The install is unable to see it. Secondly, I still have to manually press enter at startup and I have to tell it language, keyboard type etc. 
I haven't even been able to get SSH going on it yet. 
Placing the preseed file (default.txt) on the disc itself doesn't seem to do anything either, it still prompts me for everything. preseed/file=/cdrom/default.txt is what I changed it to at the append part (instead of IP).

So far - dang.

---

### Post by Lars Noodén on 2013-06-24
127.0.1.1 is the same machine that has the CD / DVD.  You need the LAN address for your web server, the laptop, which has your preseed file.  Then you have to have an  installation disc that  actually points to that file.  It would be something like [http://192.168.0.101/server.seed](http://192.168.0.101/server.seed) or whatever you named it.

---

### Post by Treekodar on 2013-06-24
I figured it out:
1. Download the ISO you want to configure
2. Edit the script found here: [http://www.utech.de/2013/05/shell-script-creating-a-cd-for-unattended-ubuntu-server-installations/](http://www.utech.de/2013/05/shell-script-creating-a-cd-for-unattended-ubuntu-server-installations/)
2a. Change it to (OBS: change 'downloads=' to the location of your iso and 'basedir=' to where you wish to save your configured iso):
```

#! /bin/bash
 
#
# General configuration
#
basedir="/home/test/Downloads/installation-scripts/ubuntu-unattended"
downloads="/home/test/Downloads"
tmpdir="${TMPDIR:-/tmp}"
builddir="$tmpdir/build.$$"
mntdir="$tmpdir/mnt.$$"
 
#
# Ubuntu release selection
#
release_name="precise"
release_version="12.04.2"
release_variant="server"
release_architecture="amd64"
 
release_base_url="http://releases.ubuntu.com"
release_base_name="ubuntu-$release_version-$release_variant-$release_architecture"
release_image_file="$release_base_name.iso"
release_url="$release_base_url/$release_name/$release_image_file"
 
#
# Target settings
#
target_base_name="${release_base_name}-auto"
target_directory="$basedir"
target_image_file="$target_base_name.iso"
 
progress() {
    echo "$*" >&2
}
 
error() {
    code="$1"; shift
    echo "ERROR: $*" >&2
    exit $code
}
 
create_directory() {
    path="$1"
    if [ ! -d "$path" ]; then
    progress "Creating directory $path..."
    mkdir -p "$path" || error 2 "Failed to create directory $path"
    fi
}
 
extract_iso() {
    archive="$1"
    if [ ! -r "$archive" ]; then
    error 1 "Cannot read ISO image $archive."
    fi
    directory="$2"
    if [ ! -d "$directory" ]; then
    mkdir "$directory" || exit 2 "Cannot extract CD to $directory"
    fi
 
    progress "Mounting image $archive (you may be asked for your password to authorize)..."
    create_directory "$mntdir"
    sudo mount -r -o loop "$archive" "$mntdir" || error 2 "Failed to mount image $archive"
 
    progress "Copying image contents..."
    cp -rT "$mntdir" "$directory" || error 2 "Failed to copy content of image $archive to $directory"
    chmod -R u+w "$directory"
 
    progress "Unmounting image $archive from $mntdir..."
    sudo umount "$mntdir"
    rmdir "$mntdir"
}
 
preset_language() {
    progress "Presetting language to 'en'..."
    echo "en" >"isolinux/lang" || error 2 "Failed to write $(pwd)/isolinux/lang"
}
 
create_kscfg() {
    if [ ! -f "ks.cfg" ]; then
    progress "Create ks.cfg file..."
    cat >"ks.cfg" <<EOF
#Generated by Kickstart Configurator
#platform=AMD64 or Intel EM64T
 
#System language
lang en_US
#Language modules to install
langsupport en_US
#System keyboard
keyboard gb_mac_intl
echo doneEOF
    fi
}
 
create_kspreseed() {
    if [ ! -f "ks.preseed" ]; then
    progress "Create ks.preseed file..."
    cat >"ks.preseed" <<EOF
d-i debconf/priority                   select critical 
d-i auto-install/enabled               boolean true 
d-i netcfg/choose_interface            select auto 
d-i netcfg/get_hostname                string obelix 
d-i network-console/password           password SECRET123 
d-i network-console/password-again     password SECRET123 
d-i preseed/early_command string anna-install network-console
EOF
    fi
}
 
patch_txtcfg() {
    (cd "isolinux";
    patch -p0 <<EOF
*** txt.cfg.orig    2013-05-14 10:06:19.000000000 +0200
--- txt.cfg 2013-05-14 10:07:54.000000000 +0200
***************
*** 2,8 ****
  label install
    menu label ^Install Ubuntu Server
    kernel /install/vmlinuz
!   append  file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet --
  label cloud
    menu label ^Multiple server install with MAAS
    kernel /install/vmlinuz
--- 2,8 ----
  label install
    menu label ^Install Ubuntu Server
    kernel /install/vmlinuz
!   append  file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz ks=cdrom:/ks.cfg preseed/file=/cdrom/ks.preseed --
  label cloud
    menu label ^Multiple server install with MAAS
    kernel /install/vmlinuz
EOF
    )
}
 
patch_isolinuxcfg() {
    (cd "isolinux";
    patch -p0 <<EOF
*** isolinux.cfg.orig   2013-05-14 10:20:37.000000000 +0200
--- isolinux.cfg    2013-05-14 10:20:50.000000000 +0200
***************
*** 2,6 ****
  include menu.cfg
  default vesamenu.c32
  prompt 0
! timeout 0
  ui gfxboot bootlogo
--- 2,6 ----
  include menu.cfg
  default vesamenu.c32
  prompt 0
! timeout 5
  ui gfxboot bootlogo
EOF
    )
}
 
modify_release() {
    preset_language && \
    create_kscfg && \
    create_kspreseed && \
    patch_txtcfg && \
    patch_isolinuxcfg 
}
 
create_image() {
    if [ ! -f "$target_directory/$target_image_file" ]; then
    if [ ! -f "$downloads/$release_image_file" ]; then
        progress "Downloading Ubuntu $release_name $release_variant..."
        curl "$release_url" -o "$downloads/$release_image_file"
    fi
    create_directory "$builddir"
    extract_iso "$downloads/$release_image_file" "$builddir"
    (cd "$builddir" && modify_release
    ) || error 2 "Failed to modify image"
 
    create_directory "$target_directory"
    progress "Creating ISO image $target_image_file..."
    mkisofs -D -r -V "UNATTENDED_UBUNTU" -cache-inodes -J -l \
        -b isolinux/isolinux.bin \
        -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 \
        -boot-info-table \
        -o "$target_directory/$target_image_file" \
        "$builddir" || error 2 "Failed to create image $target_image_file"
    if [ "x$builddir" != x -a "x$builddir" != "x/" ]; then
        rm -rf "$builddir"
    fi
    fi
}
 
create_image



```
This way you don't need a web server or anything, just pop it in and wait a bit, then SSH into it and continue the installation ;)

---

### Post by Lars Noodén on 2013-06-24
It looks like a kickstart script that modifies the preseed.  But if it works, it works.  Cool.

---

### Post by gangrene on 2013-12-19
Awesome! I was looking for something just like this, create_kscfg needs a new line for EOF and I had to put some other spaces around the place to get it to work properly but now it's perfect! 

> **Treekodar said:**
> I figured it out:
1. Download the ISO you want to configure
2. Edit the script found here: [http://www.utech.de/2013/05/shell-script-creating-a-cd-for-unattended-ubuntu-server-installations/](http://www.utech.de/2013/05/shell-script-creating-a-cd-for-unattended-ubuntu-server-installations/)
2a. Change it to (OBS: change 'downloads=' to the location of your iso and 'basedir=' to where you wish to save your configured iso):
```

#! /bin/bash
 
#
# General configuration
#
basedir="/home/test/Downloads/installation-scripts/ubuntu-unattended"
downloads="/home/test/Downloads"
tmpdir="${TMPDIR:-/tmp}"
builddir="$tmpdir/build.$$"
mntdir="$tmpdir/mnt.$$"
 
#
# Ubuntu release selection
#
release_name="precise"
release_version="12.04.2"
release_variant="server"
release_architecture="amd64"
 
release_base_url="http://releases.ubuntu.com"
release_base_name="ubuntu-$release_version-$release_variant-$release_architecture"
release_image_file="$release_base_name.iso"
release_url="$release_base_url/$release_name/$release_image_file"
 
#
# Target settings
#
target_base_name="${release_base_name}-auto"
target_directory="$basedir"
target_image_file="$target_base_name.iso"
 
progress() {
    echo "$*" >&2
}
 
error() {
    code="$1"; shift
    echo "ERROR: $*" >&2
    exit $code
}
 
create_directory() {
    path="$1"
    if [ ! -d "$path" ]; then
    progress "Creating directory $path..."
    mkdir -p "$path" || error 2 "Failed to create directory $path"
    fi
}
 
extract_iso() {
    archive="$1"
    if [ ! -r "$archive" ]; then
    error 1 "Cannot read ISO image $archive."
    fi
    directory="$2"
    if [ ! -d "$directory" ]; then
    mkdir "$directory" || exit 2 "Cannot extract CD to $directory"
    fi
 
    progress "Mounting image $archive (you may be asked for your password to authorize)..."
    create_directory "$mntdir"
    sudo mount -r -o loop "$archive" "$mntdir" || error 2 "Failed to mount image $archive"
 
    progress "Copying image contents..."
    cp -rT "$mntdir" "$directory" || error 2 "Failed to copy content of image $archive to $directory"
    chmod -R u+w "$directory"
 
    progress "Unmounting image $archive from $mntdir..."
    sudo umount "$mntdir"
    rmdir "$mntdir"
}
 
preset_language() {
    progress "Presetting language to 'en'..."
    echo "en" >"isolinux/lang" || error 2 "Failed to write $(pwd)/isolinux/lang"
}
 
create_kscfg() {
    if [ ! -f "ks.cfg" ]; then
    progress "Create ks.cfg file..."
    cat >"ks.cfg" <<EOF
#Generated by Kickstart Configurator
#platform=AMD64 or Intel EM64T
 
#System language
lang en_US
#Language modules to install
langsupport en_US
#System keyboard
keyboard gb_mac_intl
echo doneEOF
    fi
}
 
create_kspreseed() {
    if [ ! -f "ks.preseed" ]; then
    progress "Create ks.preseed file..."
    cat >"ks.preseed" <<EOF
d-i debconf/priority                   select critical 
d-i auto-install/enabled               boolean true 
d-i netcfg/choose_interface            select auto 
d-i netcfg/get_hostname                string obelix 
d-i network-console/password           password SECRET123 
d-i network-console/password-again     password SECRET123 
d-i preseed/early_command string anna-install network-console
EOF
    fi
}
 
patch_txtcfg() {
    (cd "isolinux";
    patch -p0 <<EOF
*** txt.cfg.orig    2013-05-14 10:06:19.000000000 +0200
--- txt.cfg 2013-05-14 10:07:54.000000000 +0200
***************
*** 2,8 ****
  label install
    menu label ^Install Ubuntu Server
    kernel /install/vmlinuz
!   append  file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet --
  label cloud
    menu label ^Multiple server install with MAAS
    kernel /install/vmlinuz
--- 2,8 ----
  label install
    menu label ^Install Ubuntu Server
    kernel /install/vmlinuz
!   append  file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz ks=cdrom:/ks.cfg preseed/file=/cdrom/ks.preseed --
  label cloud
    menu label ^Multiple server install with MAAS
    kernel /install/vmlinuz
EOF
    )
}
 
patch_isolinuxcfg() {
    (cd "isolinux";
    patch -p0 <<EOF
*** isolinux.cfg.orig   2013-05-14 10:20:37.000000000 +0200
--- isolinux.cfg    2013-05-14 10:20:50.000000000 +0200
***************
*** 2,6 ****
  include menu.cfg
  default vesamenu.c32
  prompt 0
! timeout 0
  ui gfxboot bootlogo
--- 2,6 ----
  include menu.cfg
  default vesamenu.c32
  prompt 0
! timeout 5
  ui gfxboot bootlogo
EOF
    )
}
 
modify_release() {
    preset_language && \
    create_kscfg && \
    create_kspreseed && \
    patch_txtcfg && \
    patch_isolinuxcfg 
}
 
create_image() {
    if [ ! -f "$target_directory/$target_image_file" ]; then
    if [ ! -f "$downloads/$release_image_file" ]; then
        progress "Downloading Ubuntu $release_name $release_variant..."
        curl "$release_url" -o "$downloads/$release_image_file"
    fi
    create_directory "$builddir"
    extract_iso "$downloads/$release_image_file" "$builddir"
    (cd "$builddir" && modify_release
    ) || error 2 "Failed to modify image"
 
    create_directory "$target_directory"
    progress "Creating ISO image $target_image_file..."
    mkisofs -D -r -V "UNATTENDED_UBUNTU" -cache-inodes -J -l \
        -b isolinux/isolinux.bin \
        -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 \
        -boot-info-table \
        -o "$target_directory/$target_image_file" \
        "$builddir" || error 2 "Failed to create image $target_image_file"
    if [ "x$builddir" != x -a "x$builddir" != "x/" ]; then
        rm -rf "$builddir"
    fi
    fi
}
 
create_image



```
This way you don't need a web server or anything, just pop it in and wait a bit, then SSH into it and continue the installation ;)

---

