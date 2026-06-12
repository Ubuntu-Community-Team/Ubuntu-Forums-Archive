---
title: "Multiple distros on nuked disk"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by nathan28 on 2011-04-11
So right now I am about to wipe a 320 gb disk and install three or four distros. Each will have a separate root partition, and will share /home (different usernames) and various /whatever data partitions.

But--what is the easiest/most painless/doesnt involve reading chapters of scripting way to ensure the bootloader works? I've spent three or four hours looking at this and right now I'm thinking I will

1. reformat the disk into the partitions from gparted live
2. install the non-Ubuntu distros
3. install Ubuntu distro as last install

Because apparently GRUB2 will automagically detect the other boot directories, and it looks like Fedora and OpenSUSE use Grub legacy.

**BUT** What's the way to keep that GRUB2 safe? I'm seeing material about dedicated MBR and dedicated GRUB partitions, but it's not noob-friendly enough for me to figure out if that partition is formatted, then manually populated, or installed to during an installation and then edited, or created during an installation. Is that partiiton tht same as /boot? Or does it point to /boot? Etc.

I'm not averse to editing by hand to point to them, but I'd prefer to have a DE/GUI up and running and grabbing packages tonight.

one of the distros will probably be Arch or Slack, but since I'm pressed for time, make-make install-configure will just have to wait.

---

