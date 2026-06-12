---
title: "Problem with script in preseed file"
date: 2022-03-17
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2022-03-17
Hi all.

I am working at a university and we look at working with an automatic OEM Ubuntu 20.04.4 iso. So far I got the automatic installation working both with full LUKS encryption and without (have different options available from grub menu).

Now we need a file populated in a local folder with an antitheft tag number (just plain text). I need to run a script that shows some kind of inputbox during the last stage of the installation. I am currently trying with zenity to show that inputbox.

in my seed-file I have this section (only part I have modified from my other seed-files)

```
ubiquity ubiquity/success_command string \
	cp /cdrom/asset.sh /target/root; \
	cp /cdrom/post-install.sh /target/root; \
	chmod 0700 /target/root/asset.sh; \
	chmod 0700 /target/root/post-install.sh; \
	in-target /root/asset.sh; \
	in-target /root/post-install.sh;
```

It seems to skip that asset.sh and don't do anything (no error messages) and just go to the part where it says that installation is complete, please remove installation media. The script asset.sh works perfectly by itself so I don't get it.
Anyone have good experience from this part that can help me?


Update: Solved it by make the script asset.sh simpler. It worked then

---

### Post by MAFoElffen on 2022-03-20
Happy to hear that you found a solution.

I'm curious about what that solution 'was'... What and how did you make it "simpler" to work from your preseed file.

---

### Post by Jaxilian on 2022-03-23
> **MAFoElffen said:**
> Happy to hear that you found a solution.

I'm curious about what that solution 'was'... What and how did you make it "simpler" to work from your preseed file.

I cut it down to this

```
#!/bin/bash
vAntiTheft=$(zenity --forms --title="Linux Platform" --text="Add number" \
   --add-entry="Enter tag number")
echo "${vAntiTheft}" > /usr/share/asset/asset.txt
```

---

### Post by MAFoElffen on 2022-03-23
Thank you! That was helpful.

---

