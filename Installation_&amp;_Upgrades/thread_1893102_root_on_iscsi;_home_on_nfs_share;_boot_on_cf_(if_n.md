---
title: "root on iscsi; /home on nfs share; /boot on cf (if needed)"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by bpmod on 2011-12-09
Hello

Here is my setup:
5 computers on LAN (more will likely be added)
1 user <brian>, as well as user <mythtv> for the MythTV stuff

1. FreeNAS 8.2
2. Mythbuntu 11.10 dedicated backend
3. Mythbuntu 11.10 dedicated frontend
4. Ubuntu 11.10 workstation
5. Windows (because there are still some things that Linux will not do)

4 of the five have gigabit LAN, the fifth (mythbuntu frontend) has 100Mbps.

The FreeNAS unit boots from a CF (read-only filesystem) and contains 10TB of storage (much more to be added as budget permits). The Windows machine has its own harddisk (I am not even *thinking* of making a diskless Windows unit). The other three (currently) have their respective OSes running on CF cards.

I would like to set it up so that the thee *buntu units can store their root filesystems on iSCSI drive(s) and their /home directories on the NFS share (so that /home is the same on all boxes). The computers that have the ability to boot from LAN would be completely diskless, and those that cannot could continue to boot from the CF card. (even if not needed, I'd like to set up at least one of each, just to do it.)

I have been reading the following:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot](https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot)
[https://help.ubuntu.com/community/Installation/OnNFSDrive](https://help.ubuntu.com/community/Installation/OnNFSDrive)
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
and many other resources, but at each step I find myself hitting walls.

The first major issue is that, (following instructions in the second link above), although the Ubuntu (and Mythbuntu) LiveCD installations find the CF card and install to it with no problems whatsoever, the Minimal install CD will not find it nor allow me to install to it. Conversely, the latter will allow me to install to an iSCSI (with no provisions for booting), while the former will not. It is the "no provisions for booting" part that has me stopped dead in my tracks. I am certain that I can set that up manually, though, if prodded in the right direction.

The next major issue (and maybe this should be asked elsewhere, but I am certain there are lots of knowledgable folks here) is that my NFS share is currently not able to be written to by root if its ownership is set to a given user, or by Windows if its ownership is set to root. I have tried getting around that by adding root to the user's group and the user to root's group, but that hasn't worked.

I have the user <brian> set up on all systems with the same password. On the Ubuntu systems, that user gets uid 1000; on the FreeNAS, it gets uid 1002, so my first order of business is to make sure that the uid and gid are the same across all systems. Should I set up an LDAP server for that? And if so, what would be the best machine to set that up on (not having the budget to put in a dedicated LDAP server)? I would really like to set up FreeNAS to also administer LDAP and DHCP, but with its read-only filesystem, that seems impossible. Please, please, let me know if it is indeed possible, even if very difficult.

Also, on FreeNAS, the wheel group is set up, but on Ubuntu, root is in the group root. Both these gid's are 0, so I don't think that poses any problem, but I'd like to know for sure.

I have spent several hours trying many different combinations of settings on the permissions and ownership of the directory that is set up as the NFS share, and here is what I am up against:

Try as I might, unless the share is 777, I cannot mkdir (as root using sudo) from any Ubuntu box with any user/group ownership of that share. If the share is owned by brian/brian, I can mkdir as brian, but not as root. Also, I cannot mkdir as brian and then chown that directory to root. So, the simplest task of creating a directory on the share to be mounted as /home so that I can copy/move the current contents of /home to it has been completely unsuccessful. I am thinking that I am overlooking something very simple.

Does there exist a tutorial that would walk me through this step-by step? I can usually figure things out without much help, but this has me completely stumped.

In summary, the important part of this poject is to have the same /home (more specifically, /home/brian) on each box, so that I do not have to go digging for files regardless of what box I happen to be using. I also have no emotional attachment to an iSCSI drive and will certainly install the root filesystem of each *buntu to a part of the NFS share if that's easier.

All suggestions and comments welcome.

Thanks

Brian

---

