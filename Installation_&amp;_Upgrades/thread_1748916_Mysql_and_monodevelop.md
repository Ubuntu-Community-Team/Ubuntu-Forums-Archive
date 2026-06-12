---
title: "Mysql and monodevelop"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Silent Miracle on 2011-05-04
i am using monodevelop 2.0 for making my project in C# asp.net. Does anyone how i can use the database of monodevelop2.0 . Also i am using Mysql and i am unable to connect my asp.net pages of monodevelop with mysql. Can anyone please guide me... like what libraries to include or any dll ... here is my code:

using System;
using System.Web;
using System.Web.UI;
using System.Data;
using MySql.Data.MySqlClient;
using MySql.Data.Types;
namespace testing_data
{
    
    
    public partial class Default : System.Web.UI.Page
    {
        string connect="Server="+localhost +";Database="+patient+"; User ID="+root+"; Password="+root;
 MySqlConnection con= new MySqlConnection(connect);
    con.Open();
    //    IDbCommand dbcmd=con.CreateCommand();
        //CREATE TABLE login(name varchar(45), password varchar(10));
        
        
        public virtual void button1Clicked(object sender, EventArgs args)
        {
            //button1.Text = "You clicked me";
            string sql = "SELECT * FROM reg";
            MySqlCommand cmd=new MySqlCommand(sql,con);
             //dbcmd.CommandText = sql;
       MySqlDataReader reader = cmd.ExecuteReader();
       while(reader.Read()) {
            string FirstName = (string) reader["name"];
            string LastName = (string) reader["password"];
            Console.WriteLine("Name: " +FirstName + " " + LastName);
       }
    }

        }
    }
}

---

