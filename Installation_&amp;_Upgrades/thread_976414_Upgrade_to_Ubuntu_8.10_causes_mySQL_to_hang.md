---
title: "Upgrade to Ubuntu 8.10 causes mySQL to hang"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by ilantal on 2008-11-09
I have an application using mySQL which worked well under ubuntu 8.04. Since the upgrade the application fails to exit. I wrote a new simple application which just makes a connection as

@Override protected void startup() {
show(new DesktopApplication1View(this));
try {
Class.forName("com.mysql.jdbc.Driver").newInstance();
dbConn = DriverManager.getConnection(
"jdbc:mysql://localhost:3306/beitKnesset", "root", "han");
}
catch(Exception e) {
e.printStackTrace();
}
}

I tried to see how it exits using

protected void end() {
try {
dbConn.close();
} catch (SQLException ex) {
Logger.getLogger(DesktopApplication1.class.getName()).log(Level.SEVERE, null, ex);
}
super.end();
}

It passes the try statement with no error, but the application stays open. If I run it from a terminal, it will not return to the command line and ^C fails to make it return.
If I remove the dbConn = DriverManager.getConnection and the dbConn.close(), then all works normally.
I tried uninstalling mySQL and reinstalling, but nothing changed.

Can anyone give me a suggestion?
THanks,
Ilan

---

