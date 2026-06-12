---
title: "Issue ecryptfs file still encrypted"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by ledhrimm on 2014-08-26
Hi ecryptfs gurus,

At first I go into trouble because of the Backup default tool automated every week. I never meant doing this with the default software after a fresh 14.04 install!? 
And for the first time I agree with the first launch of this Backup tools I was told it's over quota. 
As my disk is full. I saw files I never saw before in ".Private" that I never create neither. 
So I deleted all these Encrypt FNEK (now it smell as fenec) 

And as i cannot deleted as "me" user, I've done with sudo Power. So now I'm in trouble with ecryptfs.

I've read and try a lot of things :

bodhizazen solution
dustinkirkland
goshawknest
kaijanmaki
ubuntu wiki/forum
...

1st I use ecryptfs-recover...
And get back about twenty dir or file in ECRYPT...FNEK_something
I've try to create same user account in LiveCD mode with/without same password as my single user account in my real Ubuntu box ...

then I try quite half of the ecryptfs tools :

add-passphrase
wrap,rewrap,unwrap
ecryptfs-insert---->keyring

I'll get these:

signature not found in keyring
fopen ...

I'll try also one script found in the forum and here is the results

> 
./mount_backup_encrypted_HOME_bis.sh
Type your password:
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
Passphrase:

Signatures:
fe0a183af5e64a4a
6dd1f86c16d8792b
Should be empty:
keyring is empty
Do not type anything:
Passphrase:
Inserted auth tok with sig [ea87d0365b9dc3d5] into the user session keyring
Inserted auth tok with sig [92386840e0b0a8ee] into the user session keyring
Sould have signatures:
keyring is empty
Mounting /home/.ecryptfs/serge on /mnt/OldHome_2...
Error attempting to evaluate mount options: [-22] Invalid argument
Check your system logs for details on why this happened.
Try updating your ecryptfs-utils package, and/or
submit a bug report on [https://bugs.launchpad.net/ecryptfs](https://bugs.launchpad.net/ecryptfs)
I'll try to mount from "me" as user or as sudo
from LiveCD, from my "empty failed disk"

still encrypted files



So this result above is a kind of summary :
I get a Private.sig with 2 encoded ? that come from ?
I don't remember any use of another passphrase since the fresh install and I have no trouble before trying to gain some space and deleting files I don't recognize, mistaken with Backup tools file I guessed to be the .Private content...

So I need to recover files in this f...g /home dir in my /dev/sda5 encrypted

If gentle people could help to gave me a clean and clear process I could follow from A to z ?
what are the relation between signature file Private.sig, passphrase and the keyring (which one the user one? the session one? the sudoers one etc..)

I'm lost in the head

but Am I definitivly lost???
Will I lose my work and worst my keypassx databases!?

Hope to Thanks you 

Wiki and Docs would gain to be clearer about:
- with which user the cli command have to be executed
- order or sequences to chain commands from recover to mounting the directory
- the name are confusing passphrase 1 or 2, login, login passpharse, sudo password, password

---

### Post by ledhrimm on 2014-08-31
Ok,

nobody as ecryptfs guru 

So I do a DD iso from the whole disk just in case somebody as new tests to'll reinstall from scratch without any encryption let me try recover some of the most importants files.
And as I can't get a GUI login from my main user and only CLI login I'll will reinstall from scratch without any kind of encryption since there's not enough people to mastering this.

thanks for people that let me get hope to recover trough theirs comment, blog or forum elsewhere.

:confused:

---

