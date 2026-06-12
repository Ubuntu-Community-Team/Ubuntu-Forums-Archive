---
title: "Tagging and Segregating Packages as &quot;Items of Interest&quot;"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by ericmarceau on 2007-02-13
When scanning for packages of interest to perform a certain function, I would like to be able to mark them, not for install, but for putting them on a checklist of things to look over.

The process I visualize is as follows:

  a) open synaptic

  b) choose a section, or all

  c) scroll through the packages, examine properties

  d) discover package of interest "for future consideration"

  e) right-click on package line

  f) select "Mark as Item-of-Interest"

  g) (overkill ?) prompt for name of shortlist to track and enter (or select from existing)

  h) click on "Status" button


At this point, below the usual categories, you would find the labels for all the shortlists that have been created.  If you clicked on any of those, it would behave as if you had clicked on any of the usual categories.

For example, I want to find the perfect news aggregator.  There are many.  I would like to try them all, but not all at once.  I go through the available packages, select all that have anything to do with RSS, news, etc., and mark all of these using  "Mark as Item-of-Interest".  I save them under the shortlist label RSS.  I click on the Status button and see RSS listed below "Not installed (residual config)".  I click on the RSS item, and all the packages I marked are shown, ** and remain until I delete the shortlist **, and survives a quit from synaptic or a machine reboot.  Namely, it is saved to disk when I assign the shortlist label.

Now I can keep track of which packages have not yet been installed/tested/removed, and don't have to keep track of a separate paper or file that needs to be crossed off.

The reason why I mostly want this is because, as I search for something to do one function, I always stumble upon packages of interest, but don't want to install right away.  I lose track of those, then have to find them again.  Sometimes, I never remember what they were, and the opportunity is lost.

You could also use it as a "change management" tool, by grouping a number of distinct, but related packages together, confirming you have tracked down all "cooperating" packages, then install/test/remove/roll-back in a coordinated fashion.

I think this kind of facility within aptitude would be useful.

Most importantly, possibly using this approach, to facilitate an automated roll-back capability, would be most desirable for disciplined configuration management, within a single-host environment.  The approach **might** also simplify such management for a multi-host environment, allowing to have visibility of "change bundles (multiple packages)" to create the deltas for distribution/replication to other hosts on the network.

Do you agree that this would be of benefit to users?

Eric

---

