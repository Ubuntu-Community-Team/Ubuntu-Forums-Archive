---
title: "Ubuntu-to-Ubuntu folder sharing"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LavianoTS386 on 2008-10-11
I am trying to share my music folder on my desktop to my laptop. Both machines are running Intrepid. I've selected my music folder for sharing, but it doesn't come up on my laptop, why? 

In Hardy it was just that simple. What do I have to do now to view a folder across a network?

---

### Post by LavianoTS386 on 2008-10-12
No one else has been having problems?

---

### Post by Gina on 2008-10-12
I have had problems with file and folder sharing but I do have it working now.  I found it rather odd - sometimes setting up a folder to share worked and sometimes it didn't.  I'm planning to go through sharing setup in more detail - the way this is done has been changing so much in Intrepid and in Hardy from that in Feisty etc.  Time is my problem at present.

---

### Post by nanog on 2008-10-13
sshfs fuse is the way to go.

```
sudo apt-get install sshfs
```

create a folder that will serve as the mount point:

```
mkdir /home/xxx/Desktop/server
```

```
sudo sshfs user@xxx.xxx.xxx:/home/user /home/xxx/Desktop/server
```

this can be automated on startup if you use keys and add the command to your sessions. i can provide instructions if you do not know how to do this.

imo, gvfs is still far too buggy to use for remote shares (multiple backtraced unresolved bugs upstream).

---

### Post by durand on 2008-10-13
I find that gvfs works great for sftp (via ssh) and nfs shares. Too bad that the folder sharing tool only supports samba...

---

### Post by LavianoTS386 on 2008-10-13
> **nanog said:**
> sshfs fuse is the way to go.

```
sudo apt-get install sshfs
```

create a folder that will serve as the mount point:

```
mkdir /home/xxx/Desktop/server
```

```
sudo sshfs user@xxx.xxx.xxx:/home/user /home/xxx/Desktop/server
```

this can be automated on startup if you use keys and add the command to your sessions. i can provide instructions if you do not know how to do this.

Yeah I'm not sure what you mean by keys.

Do I do this on both machines?

---

### Post by nanog on 2008-10-13
> I find that gvfs works great for sftp (via ssh) and nfs shares.

I find that gvfs sftp shares crash with dbus errors after heavy use in x64. There are bugs filed in ubuntu and upstream with no resolution. Gvfs also  does not allow for access with many gui-based applications (e.g. OOo). sshfs is completely transparent and *everything* just works.

---

### Post by nanog on 2008-10-13
You issue the command on the local machine. After logon to the remote machine the local folder you created becomes the mount point. The remote filesystem is seamlessly integrated into you local filesystem. This only works if your remote share has an ssh server running. But that trivial to set up in almost any os.


A c&p that describes key-based ssh login:

Automatic login into ssh

First you&#8217;ll need to generate your local public key. This is the public end of a local public / private pair that you&#8217;ll share with the remote machine to identify you.

ssh-keygen -t dsa (on your local machine)

Second you&#8217;ll need to copy this key to the remote machine using a command such as:

scp ~/.ssh/id_dsa.pub [email]user@yourserver.com[/email]:

Lastly, log into the remote machine via ssh (using your password for the last time!) and use this command to add the newly generated key to the list of authenticated keys:

cat id_dsa.pub >> .ssh/authorized_keys

You&#8217;ll also probably want to delete the original key as well.

rm id_dsa.pub

At this point a copy of your key is now stored on the remote machine as an authorized keys and any ssh connection coming from the local machine will match that key and connect with the key authentication instead of a password. So nice.

&#8230;just remember that anyone with access to your machine will now have this access as well. Definitely keep this in mind if you&#8217;re using any kind of a public machine.

---

### Post by durand on 2008-10-14
> **nanog said:**
> I find that gvfs sftp shares crash with dbus errors after heavy use in x64. There are bugs filed in ubuntu and upstream with no resolution. Gvfs also  does not allow for access with many gui-based applications (e.g. OOo). sshfs is completely transparent and *everything* just works.

Hmmm, I suppose it could be related to x64..On sshfs, how exactly does it differ from gvfs? Is it just a fuse implementation of what gvfs does?

---

