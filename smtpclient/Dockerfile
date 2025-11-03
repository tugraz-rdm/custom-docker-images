FROM imixs/exim4:latest

COPY setup.sh /setup.sh
RUN chmod +x /setup.sh
RUN /setup.sh

RUN chmod 755 /usr/sbin/exim4 /usr/sbin \
 && chmod 777 /var/log/exim4 /var/spool/exim4 \
 && chown -R Debian-exim:Debian-exim /var/log/exim4 /var/spool/exim4 \
 && chmod -R a+r /etc/exim4

ADD run.sh /exim_start_non_root
RUN chown -R Debian-exim:Debian-exim /exim_start_non_root && chmod +x /exim_start_non_root

EXPOSE 8025

# Switch to non-root user
USER Debian-exim

ENTRYPOINT ["/exim_start_non_root"]
