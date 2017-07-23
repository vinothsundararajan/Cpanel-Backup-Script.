# cPanel Backup script.

### Here, i have updated the file script file called backup.sh. The below script which helps to take entire backup of cpanel accounts.
            
![](https://www.buycpanel.com/wp-content/uploads/2016/12/cPanel-logo.png)        


            
            
             #!/bin/bash
             IFS="$"
            
            now=$(date +"%m-%d-%Y")
            mkdir -p /mnt/backup/$now
            tempdir=/mnt/backup/$now
            targetdir=/mnt/backup
            archivefile="`date +%Y-%m-%d_%H-%M`_filename.tar"
            cd /var/cpanel/users
            
            find * | while read CPUSER; do
              echo "Now processing ${CPUSER} ..."
              /scripts/pkgacct ${CPUSER} $tempdir
              done
            # Generating single archive file
            tar -cf  ${targetdir}/${archivefile} ${tempdir}
            rm -rf $tempdir
            
Thank you.
