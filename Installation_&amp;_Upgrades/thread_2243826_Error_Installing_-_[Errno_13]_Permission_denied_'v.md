---
title: "Error Installing - [Errno 13] Permission denied: '/var/lib/partman/stopfifo'"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by aravind3 on 2014-09-11
[COLOR=#000000]Hi All,[/COLOR]

[COLOR=#000000]I am trying to install UBUNTU 14.0.4.1 LTS along with windows 8 to dual boot.[/COLOR]

[COLOR=#000000]Specs:[/COLOR]
[COLOR=#000000]Thoshiba p75-A7100[/COLOR]
[COLOR=#000000]8gb , Came installed with Windows 8.[/COLOR]

[COLOR=#000000]I am tryin to install ubuntu from a live cd. The UEFI is enabled,Secure boot is disabled. The Installer gets stuck at "Prepare to Install phase" with below stack trace in debug[/COLOR]

[COLOR=#000000]Stack trace[/COLOR]
[COLOR=#000000]---------------[/COLOR]

[COLOR=#000000](process:4250): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied. dconf will not work properly.[/COLOR]

[COLOR=#000000](process:4250): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied. dconf will not work properly.[/COLOR]

[COLOR=#000000](process:4250): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied. dconf will not work properly.[/COLOR]

[COLOR=#000000](process:4250): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused[/COLOR]

[COLOR=#000000](process:4263): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied. dconf will not work properly.[/COLOR]

[COLOR=#000000](process:4263): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied. dconf will not work properly.[/COLOR]

[COLOR=#000000](process:4263): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied. dconf will not work properly.[/COLOR]

[COLOR=#000000](process:4263): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused[/COLOR]
[COLOR=#000000]update_release_notes_label()[/COLOR]
[COLOR=#000000]update_release_notes_label()[/COLOR]
[COLOR=#000000]/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 512 was not found when attempting to remove it[/COLOR]
[COLOR=#000000]GLib.source_remove(self.timeout_id)[/COLOR]
[COLOR=#000000]/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 578 was not found when attempting to remove it[/COLOR]
[COLOR=#000000]GLib.source_remove(self.rows_changed_id)[/COLOR]
[COLOR=#000000]Exception caught in process_line:[/COLOR]
[COLOR=#000000]Traceback (most recent call last):[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 145, in process_line[/COLOR]
[COLOR=#000000]return self.dbfilter.process_line()[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 287, in process_line[/COLOR]
[COLOR=#000000]if not input_widgets[0].run(priority, question):[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 2977, in run[/COLOR]
[COLOR=#000000]size = int(parted.partition_info(p_id)[2])[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 220, in partition_info[/COLOR]
[COLOR=#000000]self.open_dialog('PARTITION_INFO', partition)[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 141, in open_dialog[/COLOR]
[COLOR=#000000]self.error_handler()[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 112, in error_handler[/COLOR]
[COLOR=#000000]exception_type = self.read_line()[0][/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 74, in read_line[/COLOR]
[COLOR=#000000]line = self.outf.readline().rstrip('\n')[/COLOR]
[COLOR=#000000]File "/usr/lib/python3.4/codecs.py", line 313, in decode[/COLOR]
[COLOR=#000000](result, consumed) = self._buffer_decode(data, self.errors, final)[/COLOR]
[COLOR=#000000]UnicodeDecodeError: 'utf-8' codec can't decode byte 0xd5 in position 66: invalid continuation byte[/COLOR]
[COLOR=#000000]Exception ignored in: <bound method PartedServer.__del__ of <ubiquity.parted_server.PartedServer object at 0x7f86ed2fbf28>>[/COLOR]
[COLOR=#000000]Traceback (most recent call last):[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 62, in __del__[/COLOR]
[COLOR=#000000]self.close_dialog()[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 148, in close_dialog[/COLOR]
[COLOR=#000000]self.sync_server()[/COLOR]
[COLOR=#000000]File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 132, in sync_server[/COLOR]
[COLOR=#000000]with open(stopfifo, 'w'):[/COLOR]
[COLOR=#000000]PermissionError: [Errno 13] Permission denied: '/var/lib/partman/stopfifo'[/COLOR]

[COLOR=#000000]Screenshot Of Partition[/COLOR]
[COLOR=#000000]---------------------------------[/COLOR]

[COLOR=#000000]Attached as i am not able to paste here.[/COLOR]

[COLOR=#000000]Please give some guidance on how to solve this. i am stuck on this for like 3 days now.[/COLOR]

---

### Post by Elfy on 2014-09-11
Thread closed. Please do not post duplicates, it dilutes community effort.

---

