---
title: "Error on Upgrade * Ubuntu 7.10"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by cybernet on 2008-03-18
/var/lib/scrollkeeper/sv/scrollkeeper_extended_cl.xml:2806: parser error : attributes construct error
      <sect category      </sect>
                          ^
/var/lib/scrollkeeper/sv/scrollkeeper_extended_cl.xml:2806: parser error : Couldn't find end of Start Tag sect line 2806
      <sect category      </sect>
                          ^
/var/lib/scrollkeeper/sv/scrollkeeper_extended_cl.xml:2941: parser error : Opening and ending tag mismatch: sect line 1655 and ScrollKeeperContentsList
</ScrollKeeperContentsList>
                           ^
/var/lib/scrollkeeper/sv/scrollkeeper_extended_cl.xml:2942: parser error : Premature end of data in tag sect line 1485

^
/var/lib/scrollkeeper/sv/scrollkeeper_extended_cl.xml:2942: parser error : Premature end of data in tag ScrollKeeperContentsList line 2




what is wrong :confused:

---

### Post by erginemr on 2008-03-19
Assuming from your signature that you are using Edgy:

You cannot upgrade directly from Edgy(6.10) to Gutsy(7.10). You should upgrade first to Feisty(7.04), and then to Gutsy. So it should be like this:
Edgy (with all updates) -> Feisty (with all updates) -> Gutsy.

But I suggest you to back up your personal data (and your /home and /etc) folders to a removable medium and do a clean install of Gutsy to avoid numerous problems.

---

