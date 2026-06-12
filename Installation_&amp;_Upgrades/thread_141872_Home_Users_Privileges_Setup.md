---
title: "Home Users Privileges Setup"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2006-03-09
I'm setting up Breezy on a PC that will be used by the family and I have some questions regarding how I may set up the user accounts to do what I want. :confused: 

The system is to handle 2 adults and 2 kids.

[INDENT]1 adult (me) is technically adequate (IMHO)
1 adult (spouse) is, .. um... _not_ technically-inclined, so everything has to be made as fairly easy.
2 kids (3 at < 6 years old) are probably going to surpass my spouse rather quickly ;) [/INDENT]

I set up 2 groups; adult and kids and have 3 areas which I want to set the privaledges for differently between the groups.

[1] _We have shared folders off of the /home/ directory _( /home/multimedia, /home/pictures & /home/music ). I want the adult users to be able to read/write to the shared folders and grant the kids read-only access (*reduce accidentally hitting the "delete" key or moving things where we'll never find them again*)

I think it is a case of making the owner *root* and the group *adult*, giving the owner and group read/write and all else read-only permissions.

[2] _We have dial-up internet connection at this time._ I want the adults users to be able to access the internet (prompting for sudo password is fine) but either have the kids (1) unable to, or (2) able to but need to enter a local password which the adults can enter (not the more complicated password we use for the account).

Eventually they will need access to the internet but not to other *adult* privelages.

*I know a lot of this may be irrelevant since it was Windows98 that was always prompting to go online and it was so easy for anybody to not pay attention, hit <Enter> and who knows WHAT is being sent out!*

[3] _I want to seperate an admin account for updates/installs._ It won't kill me if I have to give myself these rights, and I may even be willing to have my spouse have these rights, but I want to buffer it from the kids (and honestly, my spouse).

So I think in summary my needs are :
[LIST]
[*]Internet connection / read-write files / system admin (local admin)
[*]Internet connection / read-write files / no system admin (adults)
[*]Internet connection / read-only files / no system admin (older kids)
[*]no Internet connection / read-only files / no system admin (kids)
[/LIST]

Is this a good scheme, or am I getting too complicated over nothing?
Is there a better scheme?
How would I set up the controls for each of these?

Thanks.
p.s. I would be intersted in hearing how other families have their user accounts set up.

---

### Post by cilynx on 2006-03-09
It sounds to me like you already know what you're talking about.  Effective privelege seperation is one of the great things in the *NIX world.  I think your schema setup is quite effective.

Your shared folders don't need to be owned by root.  They can be owned by one of the adult users.  Could be root as well, just not necessary.  Just make sure that the groups and group permissions are setup and you won't have a problem.

As for the internet connection, you're good with sudo password on your end, why not just use that to deter the kids as well?  Or is that what you mean by "not the more complicated password we use for the account"?  Dial-up networking is one of the things you can grant / remove on a user level in the Users and Groups control panel.  All you have to do is make sure that the kids don't have access right now, but when they're old enough to have the responsibility, grant Dial-up networking access in the admin panel.  All they will need is their own sudo password to access it then.

As for a separate admin account, it's called "root".  But seriously, if you want to make a higher level account that still isn't root, you can easily add a new user and just check all of the access boxes in the Users and Groups panel.  Personally, I just use my normal account for administration and "sudo -s" my way up to root when entirely necessary.

I hope this helps...

---

### Post by Dragonbite on 2006-03-09
For the folders I thought using root as the owner because there's very little chance of THAT account being deleted!

For the internet connection, isn't the sudo password the same as the user's account (and therefor if they can log in, they can use that password for the sudo password prompt as well)?

---

### Post by cilynx on 2006-03-09
The sudo password is the same as the account password, yes, but it won't get them anywhere if you don't allow their account access to Dial-up networking in the Users and Groups admin panel

---

### Post by Dragonbite on 2006-03-09
Oh, ok. Thanks for the info, can't wait to give it a try when I get home!

---

