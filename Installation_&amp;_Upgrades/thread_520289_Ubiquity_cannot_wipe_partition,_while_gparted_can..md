---
title: "Ubiquity cannot wipe partition, while gparted can..."
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by smartboyathome on 2007-08-08
I am running not ubuntu itself, but a DVD made by a friend (Salocin Linux). I could not burn to a dvd (due to the bug in ubuntu), but I managed to boot it with luck due to xubuntu booting from the extracted version of it on my HD. Anyway, I got tired of using it from my HD (due to it using up all the space on the drive when running), so I tried installing it using Ubiquity when, surprise!, it would not install because:
"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?"

When I tried erasing that partition using Gparted, it worked, so I am guessing it is a bug in Ubiquity. In case it helps, here is what I get when this error comes up:
```

Aug  7 22:22:23 ubiquity: partition_cache end
Aug  7 22:22:34 ubiquity: Partman: state = [['', None, None]]
Aug  7 22:22:34 ubiquity: ['log-output', '-t', 'ubiquity', '--pass-stdout', '/bin/partman'] exited with code 0
Aug  7 22:22:35 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/migration-assistant/ma-ask', '/usr/lib/ubiquity/migration-assistant']' for ubiquity.components.migrationassistant.MigrationAssistant
Aug  7 22:22:35 ubiquity: Watching for question patterns ^migration-assistant/partitions, ^migration-assistant/.*/users$, ^migration-assistant/.*/items$, ^migration-assistant/.*/user$, ^migration-assistant/.*/password$, ^migration-assistant/failed-unmount, ERROR
Aug  7 22:22:37 ubiquity: ['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/migration-assistant/ma-ask', '/usr/lib/ubiquity/migration-assistant'] exited with code 0
Aug  7 22:22:52 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/migration-assistant/ma-ask', '/usr/lib/ubiquity/migration-assistant']' for ubiquity.components.migrationassistant.MigrationAssistant
Aug  7 22:22:52 ubiquity: Watching for question patterns ^migration-assistant/partitions, ^migration-assistant/.*/users$, ^migration-assistant/.*/items$, ^migration-assistant/.*/user$, ^migration-assistant/.*/password$, ^migration-assistant/failed-unmount, ERROR
Aug  7 22:22:55 ubiquity: ['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/migration-assistant/ma-ask', '/usr/lib/ubiquity/migration-assistant'] exited with code 0
Aug  7 22:22:55 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/user-setup/user-setup-ask', '/target']' for ubiquity.components.usersetup.UserSetup
Aug  7 22:22:55 ubiquity: Watching for question patterns ^passwd/user-fullname$, ^passwd/username$, ^passwd/user-password$, ^passwd/user-password-again$, ERROR
Aug  7 22:22:59 ubiquity: ['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/user-setup/user-setup-ask', '/target'] exited with code 0
Aug  7 22:23:00 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
Aug  7 22:23:00 ubiquity: Watching for question patterns ^partman/confirm.*, type:boolean, ERROR, PROGRESS, ^ubiquity/summary.*
Aug  7 22:23:00 ubiquity: ['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/share/ubiquity/summary'] exited with code 0
Aug  7 22:23:03 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/bin/partman-commit']' for ubiquity.components.partman_commit.PartmanCommit
Aug  7 22:23:03 ubiquity: Watching for question patterns ^partman/confirm.*, type:boolean, ERROR, PROGRESS

```

Please help so I can install this!!!

---

### Post by smartboyathome on 2007-08-08
bump!

---

