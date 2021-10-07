# frozen_string_literal: true

# Sometimes it's a README fix, or something like that - which isn't relevant for
# including in a project's CHANGELOG for example
# TODO: check if it might be just removed
declared_trivial = github.pr_title.include? '#trivial' # rubocop:disable Lint/UselessAssignment

# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn('PR is classed as Work in Progress') if github.pr_title.include? '[WIP]'
# warn('No assignee') if github.pr_assignee.nil?

# Warn when there is a big PR
warn('Big PR') if git.lines_of_code > 500
error('Too big PR') if git.lines_of_code > 9000

# Don't let testing shortcuts get into master by accident
raise('fdescribe left in tests') if `grep -r fdescribe specs/ `.length > 1
raise('fit left in tests') if `grep -r fit specs/ `.length > 1
