---
title: "Dual boot install fail, &quot;??? ???&quot; Error. Fault by raid?"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by Daniel_Edin on 2014-09-01
[COLOR=#000000]Hello I'm trying to dual boot Ubuntu on my Acer s7-392 (this computer has two SSD's in raid 0) but I am experiencing difficulties. [/COLOR]


[COLOR=#000000]I have stored the recovery partition to a USB-drive, and cleared the partition (16Gb) for installing Ubuntu.

I am using another USB-stick for the installation, I used Universal USB installer and made myself a bootable USB along with the 64-bit ISO file. I have also disabled fast boot and secure boot.

After assigning a root ext4 partition along with a swap area and proceeding to the next step I get a "??? ???" error message pushing me back to the partitioning screen and failing the installation. [/COLOR]

[COLOR=#000000]I have tried different boot loader devices but they all give the same error.[/COLOR]

[COLOR=#000000]I tried updating the bios but it did not change anything. Also tried disabling RAID in bios but I still get this "??? ???" error.  

I ran a bootinfoscript as well, the result is in the RESULTS.txt. I don't know if that will help.

One more thing, the installer doesn't recognize the Windows installation.

[/COLOR][ATTACH=CONFIG]256055[/ATTACH],[ATTACH=CONFIG]256056[/ATTACH], [ATTACH=CONFIG]256057[/ATTACH], [ATTACH=CONFIG]256058[/ATTACH],  [ATTACH]256059[/ATTACH][COLOR=#000000]

Any help is much appreciated![/COLOR]

---

### Post by yancek on 2014-09-01
The images you posted show several ntfs/windows partitions under the Installation Type window as well as in GParted.  I don't use RAID so can't help but someone should be along to help.

---

### Post by Daniel_Edin on 2014-09-02
> **yancek said:**
> The images you posted show several ntfs/windows partitions under the Installation Type window as well as in GParted.  I don't use RAID so can't help but someone should be along to help.

Yeah it does recognize the partitions of windows.

I assume you should choose "Device for boot loader installation" the one that is flagged with boot, however this partition exists in three places in that list, which is confusing. I've tried them all but I still get the same error.


Is there anyway to see what exactly goes wrong with the installation? Via a log file or something?

---

### Post by Daniel_Edin on 2014-09-07
Okay so via the system log application in the log /installer/debug I found this:

"
[SIZE=1]Ubiquity 2.18.8


(ubiquity:4276): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed


(process:4309): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4309): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4309): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4309): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:4321): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4321): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4321): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4321): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:4337): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4337): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4337): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4337): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:4353): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4353): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4353): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4353): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:4372): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4372): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4372): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:4372): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 212 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 254 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
update_release_notes_label()
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 702 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 722 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 1732 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 1758 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 3067 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 3095 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(ubiquity:4276): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed


(process:23697): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23697): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23697): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23697): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:23709): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23709): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23709): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23709): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:23721): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23721): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23721): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23721): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:23737): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23737): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23737): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23737): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused


(process:23749): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23749): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23749): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.


(process:23749): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 5724 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 5807 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)"[/SIZE]

---

### Post by colo3 on 2014-12-07
Did you find a solution to the problem??

---

