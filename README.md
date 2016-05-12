This is the original plugin, except minor changes for [redmine in Debian Jessie/8.x](https://packages.debian.org/jessie/redmine)

Short docs for Debian Jessie/8.x .deb based setups

## install

```bash
cd /usr/share/redmine/
git clone https://github.com/phaidros7/due_date_reminder.git plugins/due_date_reminder
cd plugins/due_date_reminder
git checkout phaidros7-debian-jessie
#bundle install
```

```bash
cd /usr/share/redmine/
bundle exec rake redmine:plugins:migrate RAILS_ENV=production
service apache2 restart
```

## test it
```bash
cd /usr/share/redmine/
bundle exec rake redmine:reminder_plugin:send_notifications RAILS_ENV=production
```

## croni-fy
```bash
crontab -e
0 5 * * * cd /usr/share/redmine/ && bundle exec rake redmine:reminder_plugin:send_notifications RAILS_ENV=production &> /tmp/redmine_due_date_reminder.log
```


## See [original docs](/f0y/due_date_reminder) !!
