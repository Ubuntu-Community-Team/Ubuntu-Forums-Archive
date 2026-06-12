---
title: "Are we going to get large packages when updating from alpha 6 to Beta?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dadedo123 on 2009-09-30
Or will the beta just include the updates we've already updates earlier before?

---

### Post by alphacrucis2 on 2009-09-30
> **dadedo123 said:**
> Or will the beta just include the updates we've already updates earlier before?

No. If you are running Alpha 6 updated to current then you virtually have the beta already. It is just a snapshot.

---

### Post by lonniehenry on 2009-09-30
Should have only a few updates. You would probably have about the same number that you would see in a normal day's update or perhaps even less.  The beta release is a point when some people who haven't tried karmic will jump in and install.  Most of the major breakage will be over and it hopefully will be only bugfixes and polishing till the release.

---

### Post by dadedo123 on 2009-09-30
> **lonniehenry said:**
> Should have only a few updates. You would probably have about the same number that you would see in a normal day's update or perhaps even less.  The beta release is a point when some people who haven't tried karmic will jump in and install.  Most of the major breakage will be over and it hopefully will be only bugfixes and polishing till the release.

but I still get a grub menu with lots of errors. :p 
and my UNR windows have no frames when maximised!
The audio manager is not detecting my internal mic too.

---

### Post by psyke83 on 2009-09-30
It's more significant than "a few" updates. If you install from Alpha 4, I would imagine you would need to download at least 200-300mb of updates, perhaps?

---

### Post by kansasnoob on 2009-09-30
Based on previous experience you'll see somewhat of a flood of updates the first 48 hours or so because most non-critical updates are held back for a day or two while they create an acceptable iso.

It'll be manageable, and (based on prior outcome) probably pleasurable.

---

### Post by Sophont on 2009-09-30
Here we go again :-)

The Alpha and beta snapshots - are just that - snapshots.

New packages come in almost every day - sometimes a couple - sometimes dozens.

At particular days the then current state of packages in the repository is used to make an alpha or beta iso.

Somebody installing from a Alpha 3 CD and then upgrading has the same packages as somebody else who installed Alpha 6 and updated since then.

And on the day beta is "released" both will already have the same packages as somebody who installs fresh from the the beta CD.

---

### Post by Aearenda on 2009-10-01
The main thing I have noticed in the past is that the repo servers get overloaded by people who wait for the beta (or even worse, release) to be announced, and so updates take longer or even fail on 'the day'. It is much better to be absolutely up to date the day before, when the flow of updates reduces to a trickle, and then you can avoid the scrum.

---

### Post by jocko on 2009-10-01
> **Aearenda said:**
> The main thing I have noticed in the past is that the repo servers get overloaded by people who wait for the beta (or even worse, release) to be announced, and so updates take longer or even fail on 'the day'.
That may be true, but that means most people misunderstand what the "alpha 6" or "beta" is. The different alpha and beta are just stages of the development, when the development have reached a certain level of completion. When the beta is announced, the packages are already in the repo, and has been for days, weeks or months. The updates come **between** the alpha/beta announcements, **not** as part of them. The repos are even frozen for a couple of days before the announcement to make sure all packages in the repos work together and produce a functional set of CD images. Once the beta is announced, the repos are unfrozen to allow normal updates again. This is when people start complaining that "the beta just contained a few uninteresting packages"...

So. If you installed from an alpha 6 cd and kept up to date, you already have all packages that will be in the beta when it's announced later today. The only exceptions would be last-minute fixes for serious errors that breaks the install CD's. Once the beta is released, you will start to get normal updates again.

---

### Post by slakkie on 2009-10-01
Very clear post jocko.

To get some of the confusion out of the air, they should update the lsb_release to include the stage.

Now it says:
```

Description:    Ubuntu karmic (development branch)

```

It should say something like
```

Description:    Ubuntu karmic (development branch, Alpha 6)

```

That way people will see directly in which state they are. So you don't get posts.. "No updates, I can't get into $stage!! OMG".

---

