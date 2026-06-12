---
title: "Ubuntu Server multipath problem"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by rawad on 2010-12-11
am using ubuntu 10.04 LTS installed on blade server attached to DS4700 IBM SAN Storage.

i have already installed multipath-tools and created the multipath.conf file and my file is as the following
defaults {
       udev_dir /dev
       getuid_callout  "/lib/udev/scsi_id -g -u -d /dev/%n"
       user_friendly_names yes
}

blacklist {
       devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st)[0-9]*"
       devnode "^hd[a-z][[0-9]*]"
       devnode "^sd[a-z][[0-9]*]"
       devnode "^cciss!c[0-9]d[0-9]*[p[0-9]*]"
}
multipaths {
	    multipath {
	        wwid    3600a0b800050f14000000c694c68e051
	        alias   Part1
}
 	   multipath {
		wwid    3600a0b800050f13e00000d594c68e138
		alias	Part2
	    }
	}
devices {
        device {
                vendor "IBM"
                product "DS4700"
                hardware_handler "1 rdac"
                features "1 queue_if_no_path"
                path_checker rdac
                path_grouping_policy group_by_prio
                prio_callout "/sbin/mpath_prio_rdac /dev/%n"
                failback immediate
                getuid_callout  "/lib/udev/scsi_id -g -u -d /dev/%n"
        }
}

after rebooting the server the hard drives still doubling, and when am running multipath -l it shows the following:

root@DC:~# multipath -l
Part1 (3600a0b800050f13e00000d594c68e138 ) dm-1 IBM     ,1814      FASt
[size=50G][features=0][hwhandler=0]
\_ round-robin 0 [prio=0][active]
 \_ 0:0:0:1 sdb 8:16  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 1:0:0:1 sdd 8:48  [active][undef]
Part2 (3600a0b800050f14000000c694c68e051) dm-0 IBM     ,1814      FASt
[size=10G][features=0][hwhandler=0]
\_ round-robin 0 [prio=0][active]
 \_ 0:0:0:0 sda 8:0   [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 1:0:0:0 sdc 8:32  [active][undef]

when am running the command multipath -ll is shows the following:

root@DC:~# multipath -ll
Part1 (3600a0b800050f13e00000d594c68e138 ) dm-1 IBM     ,1814      FASt
[size=50G][features=0][hwhandler=0]
\_ round-robin 0 [prio=1][active]
 \_ 0:0:0:1 sdb 8:16  [active][ready]
\_ round-robin 0 [prio=1][enabled]
 \_ 1:0:0:1 sdd 8:48  [active][ready]
Part2 (3600a0b800050f14000000c694c68e051) dm-0 IBM     ,1814      FASt
[size=10G][features=0][hwhandler=0]
\_ round-robin 0 [prio=1][active]
 \_ 0:0:0:0 sda 8:0   [active][ready]
\_ round-robin 0 [prio=1][enabled]
 \_ 1:0:0:0 sdc 8:32  [active][ready]

how can i solve this problem?

---

