# clonewp
A bash script to clone a production WordPress install to a local development version.

The author is hosting websites on SiteGround and developing locally in [Varying Vagrant Vagrants](https://varyingvagrantvagrants.org/) (VVV).

This script should work in other setups too, as long as you have ssh access to the live server. Some instructions below pertains to VVV, though.

## Usage

Clone the repository into the root of your local WordPress installation:

     $ cd /Users/username/vagrant_local/www/example_site/public_html
     $ git clone git@github.com:prikkprikkprikk/clonewp.git

Then edit the settings in clonewp.yml. The file is well commented and should be self-explanatory.

Lastly, ssh into the Vagrant box and execute the script.

     $ vagrant ssh
     $ cd /srv/www/example_site/public_html
     $ clonewp/clonewp

Have a sip of your favorite beverage while the script …

* connects to your live server,
* exports the database into wp-content/uploads/db.sql,
* rsyncs wp-content into your local WordPress installation,
* deletes the remote export,
* gets the correct table prefix from the remote wp-config.php,
* imports the database,
* replaces live URLs with local URLs,
* flushes the cache, and finally
* deactivates any unneeded plugins listed in the config file.

Subsequent runs of the script will take much shorter time than the first one, due to rsync's syncing capabilities.

This script is open source and published with the GNU GPL license. Feel free to contribute!
