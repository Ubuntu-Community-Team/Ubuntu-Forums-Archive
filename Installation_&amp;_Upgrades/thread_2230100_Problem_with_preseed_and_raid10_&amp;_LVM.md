---
title: "Problem with preseed and raid10 &amp; LVM"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by maximus3 on 2014-06-17
Hello!

I have a problem with auto install ubunti server (LTS edition) based on Preseed.
Problem with parman. I want 2 primary volumes with RAID 10 if my computer have 4 disks and if comp have only 2 disk use RAID1.
With RAID1 I have problem with empty LVM, how can I skip this screen?
With RAID10 I have another problem :
main-menu[536]: proccess ... : /lib/partman/check...  :line 42 can't open /var/lib/partman/outfifo: no such file

There is my preseed config:
```

d-i keyboard-configuration/xkb-keymap select us

# Hostname
d-i netcfg/get_hostname string ($HOSTNAME)

# Mirrors
d-i mirror/country string manual
d-i mirror/http/hostname string mirror.yandex.ru
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string ($HTTPPROXYv4)
d-i mirror/suite string precise

# Passwords
d-i passwd/root-login boolean true
d-i passwd/make-user boolean false
d-i passwd/root-password-crypted password ($PASS_CRYPT)

d-i clock-setup/utc boolean true
d-i time/zone string Europe/Moscow

d-i preseed/early_command string anna-install parted-udeb


# Partitioning
d-i partman/exception_handler_note note
d-i partman/early_command string \
HSHORT=$(echo "($HOSTNAME)" | cut -d. -f1) ;\
echo "${HSHORT}" > /etc/hostname ;\
sed -i "s/^($IP).*/($IP) ($HOSTNAME) ${HSHORT}/" /etc/hosts ;\
for DISK in $(list-devices disk); do \
	dd if=/dev/zero of=${DISK} bs=512 count=1; \
	parted -s ${DISK} mklabel gpt; \
done; \
set $(list-devices disk); \
let numb=$#/2; \
DISKA=$1; \
DISKB=$2; \
DISKC=$3; \
DISKD=$4; \
USE_RAID1=no ;\
USE_RAID10=no ;\
if [ $# -eq 2 ]; then \
    USE_RAID1=yes ;\
elif [ $# -eq 4 ]; then \
    USE_RAID10=yes ;\
fi ;\
debconf-set partman-basicfilesystems/choose_label gpt ;\
debconf-set partman-partitioning/choose_label gpt ;\
debconf-set partman-basicfilesystems/default_label gpt ;\
debconf-set partman-partitioning/default_label gpt ;\
debconf-set partman-partitioning/choose_label gpt ;\
if [ "${USE_RAID1}" = "yes" ]; then \
	debconf-set partman-auto/disk "${DISKA} ${DISKB}";\
	debconf-set partman-auto/method "raid";\
	debconf-set partman-auto/expert_recipe "multiraid :: \
		1 1 1 free $gptonly{ } $primary{ } $bios_boot{ } method{ biosgrub } . \
		2500 500 2500 raid $gptonly{ } method{ raid } . \
		500  500 1000000000 ext3 $defaultignore{ } $gptonly{ } $primary{ } method{ lvm } . ";\
	debconf-set partman-auto-raid/recipe " \
		1 2 0 ext4 / ${DISKA}2#${DISKB}2 . \
		1 2 0 lvm - ${DISKA}3#${DISKB}3 . ";\
	debconf-set grub-installer/bootdev "${DISKA} ${DISKB}";\
elif [ "${USE_RAID10}" = "yes" ]; then \
    debconf-set partman-auto/disk "${DISKA} ${DISKB} ${DISKC} ${DISKD}" ;\
    debconf-set partman-auto/method "raid";\
    debconf-set partman-auto/expert_recipe "multiraid :: \
		1 1 1 free $gptonly{ } $primary{ } $bios_boot{ } method{ biosgrub } . \
		2500 500 2500 raid $gptonly{ } method{ raid } . \
		5000 500 1000000000 ext3 $defaultignore{ } $gptonly{ } $primary{ } method{ lvm } . ";\
	debconf-set partman-auto-raid/recipe " \
		10 4 0 ext4 / ${DISKA}2#${DISKB}2${DISKC}2#${DISKD}2 . \
		10 4 0 lvm - ${DISKA}3#${DISKB}3${DISKC}3#${DISKD}3 . ";\
	debconf-set grub-installer/bootdev "${DISKA} ${DISKB} {DISKC} {DISKD}";\
else \
        debconf-set partman-auto/disk "${DISKA}";\
        debconf-set partman-auto/method "regular";\
        debconf-set partman-auto/expert_recipe "boot-root :: \
	        1 1 1 free $gptonly{ } $primary{ } $bios_boot{ } method{ biosgrub } . \
		5000 500 100000000 ext4 $gptonly{ } $primary{ } filesystem{ ext4 } mountpoint{ / } use_filesystem{ } method{ format } format{ } . ";\
        debconf-set grub-installer/bootdev "${DISKA}";\
fi

partman-partitioning    partman-partitioning/confirm_new_label  boolean true
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-md/confirm boolean true
d-i partman-md/confirm_nooverwrite boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-basicfilesystems/no_swap boolean false
mdadm-udeb      mdadm/boot_degraded     boolean true

d-i partman/mount_style select traditional

# Apt
d-i apt-setup/contrib boolean true

# Packages
d-i apt-setup/services-select multiselect security, volatile
tasksel tasksel/first multiselect ubuntu-minimal
d-i base-installer/kernel/image string linux-server
d-i pkgsel/include string openssh-server vim wget lvm2
d-i pkgsel/update-policy select none

popularity-contest popularity-contest/participate boolean false

# Grub
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true

d-i finish-install/keep-consoles boolean true
d-i finish-install/reboot_in_progress note

```

Thanks!

---

### Post by maximus3 on 2014-06-18
Up please

---

