---
title: "Help with LVM"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by erikcw on 2007-04-19
Hi,

So I did a clean install of Fiesty using the alternative cd.  I manually partitioned my harddrive as follows:

/boot
/swap
/
LVM
OLD HOME PARTITION
Free SPACE

Now that the installation is finished, it doesn't look like LVM was setup properly.  I apt-get installed lvm2, and also installed system-config-lvm.

When I try to run system-config-lvm I get this:

> 
erik@turbo:/tmp$ sudo system-config-lvm 
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in <module>
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 157, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 238, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 156, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 190, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined
erik@turbo:/tmp$ 


How do I get LVM fired up so that I can use the drive space?

Thanks for your help!
Erik

---

