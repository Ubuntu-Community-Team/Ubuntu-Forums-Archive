---
title: "&quot;no root file system is defined&quot; during 14.04 preseed"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by alexclifford47 on 2014-04-29
Hi,
I've managed to get my preseed file to boot during PXE from the network but I'm only getting as far as partitioning. No matter what I tell the partition tables file to do it thinks no root file system is defined. I've tried LVM, regular partitioning, atomic/home/multi. No luck. Can anyone spot what I'm missing or suggest what I could try next?

This is my current preseed file:
```
<%#
kind: provision
name: Community Preseed
oses:
- Ubuntu 12.04
- Ubuntu 12.10
- Ubuntu 14.04
%>
<%
  # safemode renderer does not support unary negation
  pm_set = @host.puppetmaster.empty? ? false : true
  puppet_enabled = pm_set || @host.params['force-puppet']
%>
# Locale, country and keyboard settings
d-i debian-installer/locale string en_AU
d-i console-setup/ask_detect boolean false
d-i console-setup/modelcode string pc105
d-i console-setup/variant USA
d-i console-setup/layout USA
d-i console-setup/layoutcode string us

<% if @host.operatingsystem.name == 'Debian' && @host.operatingsystem.major.to_i >= 7 -%>
d-i keymap select us
<% end -%>

<% if @static -%>
# Static network configuration.
d-i netcfg/disable_dhcp boolean true
d-i netcfg/get_ipaddress string <%= @host.ip %>
d-i netcfg/get_netmask string <%= @host.subnet.mask %>
d-i netcfg/get_nameservers string <%= [@host.subnet.dns_primary,@host.subnet.dns_secondary].reject{|n| n.blank?}.join(' ') %>
d-i netcfg/get_gateway string <%= @host.subnet.gateway %>
d-i netcfg/confirm_static boolean true
<% end -%>

# Network configuration
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string <%= @host %>
d-i netcfg/get_domain string <%= @host.domain %>
d-i netcfg/wireless_wep string

d-i hw-detect/load_firmware boolean true

# Mirror settings
d-i mirror/country string manual
d-i mirror/http/hostname string <%= @preseed_server %>
d-i mirror/http/directory string <%= @preseed_path %>
d-i mirror/http/proxy string
d-i mirror/codename string <%= @host.operatingsystem.release_name %>
d-i mirror/suite string <%= @host.operatingsystem.release_name %>
d-i mirror/udeb/suite string <%= @host.operatingsystem.release_name %>

# Time settings
d-i clock-setup/utc boolean true
d-i time/zone string <%= @host.params['time-zone'] || 'UTC' %>

# NTP
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server string <%= @host.params['ntp-server'] || 'ntp.int.dc.au.ubimet.com' %>

# Set alignment for automatic partitioning
# Choices: cylinder, minimal, optimal
#d-i partman/alignment select cylinder

<%= @host.diskLayout %>

# Install different kernel
#d-i base-installer/kernel/image string linux-server

# User settings
d-i passwd/root-password-crypted password <%= root_pass %>
user-setup-udeb passwd/root-login boolean true
d-i passwd passwd/make-user boolean false
user-setup-udeb passwd/make-user boolean false

<% if puppet_enabled && @host.params['enable-puppetlabs-repo'] && @host.params['enable-puppetlabs-repo'] == 'true' -%>
# Puppetlabs products
d-i apt-setup/local0/repository string \
      http://apt.puppetlabs.com <%= @host.operatingsystem.release_name %> main
d-i apt-setup/local0/comment string Puppetlabs products
d-i apt-setup/local0/source boolean true
d-i apt-setup/local0/key string http://apt.puppetlabs.com/pubkey.gpg
# Puppetlabs dependencies
d-i apt-setup/local1/repository string \
      http://apt.puppetlabs.com <%= @host.operatingsystem.release_name %> dependencies
d-i apt-setup/local1/comment string Puppetlabs dependencies
d-i apt-setup/local1/source boolean true
d-i apt-setup/local1/key string http://apt.puppetlabs.com/pubkey.gpg
<% end -%>

# Install minimal task set (see tasksel --task-packages minimal)
tasksel tasksel/first multiselect minimal

<% if puppet_enabled %>
  <% if @host.operatingsystem.name == 'Ubuntu' and @host.operatingsystem.major.to_i == 10 -%>
    <% puppet_package = 'puppet/lucid-backports' -%>
d-i apt-setup/backports boolean true
  <% else -%>
    <% puppet_package = 'puppet' -%>
  <% end -%>
<% else -%>
  <% puppet_package = '' -%>
<% end -%>

# Install some base packages
d-i pkgsel/include string <%= puppet_package %> lsb-release openssh-server
d-i pkgsel/update-policy select unattended-upgrades

popularity-contest popularity-contest/participate boolean false

# Boot loader settings
#grub-pc grub-pc/hidden_timeout boolean false
grub-pc grub-pc/timeout string 10
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true

d-i finish-install/reboot_in_progress note

d-i preseed/late_command string wget <%= foreman_url('finish') %> -O /target/tmp/finish.sh && in-target chmod +x /tmp/finish.sh && in-target /tmp/finish.sh


```

And my current partition tables file:
```
<%#
kind: ptable
name: Community Preseed Disklayout
oses:
- Ubuntu 12.04
- Ubuntu 12.10
- Ubuntu 14.04
%>

<% if @host.params['install-disk'] -%>
d-i partman-auto/disk string <%= @host.params['install-disk'] %>
<% else -%>
d-i partman-auto/disk string /dev/sda /dev/vda
<% end -%>

### Partitioning
# The presently available methods are: "regular", "lvm" and "crypto"
<% if @host.params['partitioning-method'] -%>
d-i partman-auto/method string <%= @host.params['partitioning-method'] %>
<% else -%>
d-i partman-auto/method string regular
<% end -%>

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

<% if @host.params['partitioning-method'] && @host.params['partitioning-method'] == 'lvm' -%>
# For LVM partitioning, you can select how much of the volume group to use
# for logical volumes.
d-i partman-auto-lvm/guided_size string max
<% end -%>

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /usr, /var, and /tmp partitions
<% if @host.params['partitioning-recipe'] -%>
d-i partman-auto/choose_recipe select <%= @host.params['partitioning-recipe'] %>
<% else -%>
d-i partman-auto/choose_recipe select atomic
<% end -%>

# If you just want to change the default filesystem from ext3 to something
# else, you can do that without providing a full recipe.
<% if @host.params['partitioning-filesystem'] -%>
d-i partman/default_filesystem string <%= @host.params['partitioning-filesystem'] %>
<% end %>

# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true


```

Thanks

---

